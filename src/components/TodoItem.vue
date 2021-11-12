<template>
  <li>
    <label>
      <!--除了change事件，也可以绑定click事件-->
      <!--      此处不推荐v-model写法<input type="checkbox" v-model=‘todo.id”>因为操作了props里的参数 -->
      <input type="checkbox" :checked="todo.finished" @change="handle(todo.id)"/>
      <span>{{ todo.name }}</span>
    </label>
    <button class="btn btn-danger" @click="deleteItem(todo.id)">删除</button>
  </li>
</template>

<script>
export default {
  name: "TodoItem",
  props: ['todo','changeFinished'],
  data() {
    return {
      itemName: null,
      isFinished: null
    }
  },
  methods: {
    handle: function (id) {
      this.changeFinished(id);
    },
    deleteItem:function (id){
      this.deleteItem(id);
    }
  }
}
</script>

<style scoped>
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}

li label {
  float: left;
  cursor: pointer;
}

li label li input {
  vertical-align: middle;
  margin-right: 6px;
  position: relative;
  top: -1px;
}

li button {
  float: right;
  display: none;
  margin-top: 3px;
}

li:before {
  content: initial;
}

li:last-child {
  border-bottom: none;
}
li:hover{
  color: #dddddd;
}
li:hover button{
  display: block;
}
</style>