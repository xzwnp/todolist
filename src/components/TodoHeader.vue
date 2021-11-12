<template>
    <div class="todo-header">
      <input type="text" placeholder="请输入你的任务名称，按回车键确认" @keyup.enter="add" v-model="title"/>
    </div>
</template>

<script>
import {nanoid} from 'nanoid'
export default {
  name: "TodoHeader",
  props:['addTodoItem'],
  data(){
    return{
      title:''
    }
  },
  methods:{
    //这个有个细节，由于props:['addTodoItem'],Header组件的方法add（）不能叫addTodoItem（），否则会重复定义
    add:function (){
      //数据检查，使用trim()去空格
      if (!this.title.trim()){
        return alert("输入不能为空！");
      }
      const itemObj = {id:nanoid(),name:this.title,finished:false};
      //虽然这里用的是this.,但执行者应该被认为是App组件
      this.addTodoItem(itemObj);
      //不知道为什么下面这个用不了
      // this.$emit("addTodoItem",itemObj)
      this.title ='';
    }
  }
}
</script>

<style scoped>
/*header*/
.todo-header input {
  width: 560px;
  height: 28px;
  font-size: 14px;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 4px 7px;
}

.todo-header input:focus {
  outline: none;
  border-color: rgba(82, 168, 236, 0.8);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 8px rgba(82, 168, 236, 0.6);
}

</style>
