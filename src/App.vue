<template>
  <div class="todo-container">
    <div class="todo-wrap">
      <TodoHeader :addTodoItem="addTodoItem"></TodoHeader>
      <TodoList :todos="todos"
                :changeFinished="changeFinished"
                :deleteItem="deleteItem"></TodoList>
      <TodoFoot :todos="todos"/>
    </div>
  </div>
</template>

<script>
import TodoList from "@/components/TodoList";
import TodoHeader from "@/components/TodoHeader";
import TodoFoot from "@/components/TodoFoot";

export default {
  name: 'App',
  data() {
    return {
      todos: [{id: '001', name: '吃饭', finished: false},
        {id: '002', name: '睡觉', finished: false},
        {id: '003', name: '打豆豆', finished: false},
      ],
    }
  },
  methods: {
    addTodoItem: function (todoItem) {
      //unshift类似于push，但unshift是头插，push是尾插
      this.todos.unshift(todoItem)
    },
    changeFinished: function (id) {
      this.todos.forEach((todo) => {
        if (todo.id === id) {
          todo.finished = !todo.finished;
        }
      })
    },
    deleteItem: function (id) {
      this.todos=this.todos.filter(todo => {
        todo.id !== id
      })
    }
  },
  components: {
    TodoList,
    TodoHeader,
    TodoFoot,
  }

}
</script>

<style>
/*base*/
body {
  background: #fff;
}

.btn {
  display: inline-block;
  padding: 4px 12px;
  margin-bottom: 0;
  font-size: 14px;
  line-height: 20px;
  text-align: center;
  vertical-align: middle;
  cursor: pointer;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2), 0 1px 2px rgba(0, 0, 0, 0.05);
  border-radius: 4px;
}

.btn-danger {
  color: #fff;
  background-color: #da4f49;
  border: 1px solid #bd362f;
}

.btn-danger:hover {
  color: #fff;
  background-color: #bd362f;
}

.btn:focus {
  outline: none;
}

.todo-container {
  width: 600px;
  margin: 0 auto;
}

.todo-container .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}

</style>
