<template>
  <ul class="todo-main">
    <TodoItem v-for=" todoObj in todos"
              :key="todoObj.id"
              :todo="todoObj"
              :changeFinished="changeFinished"
              :deleteItem="deleteItem"></TodoItem>
  </ul>
</template>

<script>
import TodoItem from "@/components/TodoItem";
export default {
  name: "TodoList",
  props:['todos','changeFinished','deleteItem'],
  data() {
    return {
      total: null,
      finishedCount: null,
    }
  },
  components: {
    TodoItem,
  }
}
</script>

<style scoped>
/*main*/
.todo-main {
  margin-left: 0px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0px;
}

.todo-empty {
  height: 40px;
  line-height: 40px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding-left: 5px;
  margin-top: 10px;
}
</style>