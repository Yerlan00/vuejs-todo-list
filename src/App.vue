<template>
  <div id="app">
    <h1>Todo application</h1>
    <addTodo @add-todo="addTodo" />
    <hr />
    <TodoList
      class="list"
      v-if="todos.length"
      v-bind:todos="todos"
      @remove-todo="removeTodo"
    />
    <p v-else>No todos!</p>
  </div>
</template>

<script>
import TodoList from "@/components/ToDoList";
import addTodo from "@/components/addTodo.vue";
export default {
  name: "App",
  data() {
    return {
      todos: [
        { id: 1, title: "Buy bread", completed: false },
        { id: 2, title: "Buy oil", completed: false },
        { id: 3, title: "Buy milk", completed: false },
      ],
    };
  },
  components: {
    TodoList,
    addTodo,
  },
  mounted() {
    fetch("https://jsonplaceholder.typicode.com/todos?_limit=3")
      .then((response) => response.json())
      .then((json) => {
        this.todos = json;
      });
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
    addTodo(todo) {
      this.todos.push(todo);
    },
  },
};
</script>

<style>
h1 {
  display: flex;
  justify-content: center;
}
.list {
  display: flex;
  justify-content: center;
}
p {
  display: flex;
  justify-content: center;
  font-size: 30px;
}
</style>
