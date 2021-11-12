<template>

  <div class="todo-footer" v-show="total"><!--total必为0或其他正数，其他正数转化为bool值时为真 -->
    <label>
      <input type="checkbox" :checked="isAll" @change="isCheckedAll"/>
    </label>
    <span>
          <span title="盲生，你发现了彩蛋">已完成 {{ doneTotal}}</span> / 全部{{total}}
        </span>
    <button class="btn btn-danger">清除已完成任务</button>
  </div>
</template>

<script>
export default {
  name: "TodoFoot",
  props:["todos","changeAllFinished"],
  methods:{
    //当触发@click事件时，会自动传入一个参数e，这个参数e即为事件
    isCheckedAll(e){
      this.changeAllFinished(e.target.checked);
    }
  },

  computed:{
    //操作数据的方法应当写到app组件中，但本方法仅查看，不增删改
    total(){
      return this.todos.length;
    },
    doneTotal(){
      return this.todos.filter(todo=>{
        return todo.finished
      }).length
    },
    isAll(){
      return this.total===this.doneTotal && this.total>0;
    }
  }

}
</script>

<style scoped>
/*footer*/
.todo-footer {
  height: 40px;
  line-height: 40px;
  padding-left: 6px;
  margin-top: 5px;
}

.todo-footer label {
  display: inline-block;
  margin-right: 20px;
  cursor: pointer;
}

.todo-footer label input {
  position: relative;
  top: -1px;
  vertical-align: middle;
  margin-right: 5px;
}

.todo-footer button {
  float: right;
  margin-top: 5px;
}

</style>