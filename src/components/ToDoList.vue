<template>
  <div>
    <ul>
      <TodoItem
        v-for="(todo, index) in todos"
        v-bind:key="index"
        v-bind:index="index"
        v-bind:todo="todo"
        v-on:remove-todo="removeTodo"
      />
    </ul>
  </div>
</template>

<script>
import TodoItem from "@/components/ToDoItem.vue";
export default {
  props: ["todos"],
  components: {
    TodoItem,
  },
  methods: {
    removeTodo(id) {
      this.$emit("remove-todo", id);
    },
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  padding: 0;
  margin: 0;
}
</style>
