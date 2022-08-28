<template>
  <h1 class="text-xl font-bold pt-2">Todos</h1>
  <div class="flex items-center justify-between mt-2">
    <span>Double Click to mark as complete</span>
    <span class="flex items-center justify-between font-semibold">
      <span
        class="inline-block mr-1 w-4 h-4 bg-gradient-to-r from-green-600 to-green-500"
      ></span>
      = Incomplete
    </span>
    <span class="flex items-center justify-between font-semibold">
      <span
        class="inline-block mr-1 w-4 h-4 bg-gradient-to-r from-gray-500 to-gray-600"
      ></span>
      = Complete
    </span>
  </div>
  <div class="grid grid-cols-2 sm:grid-cols-2 md:grid-cols-3 gap-4 mt-4">
    <div
      @dblclick="onUpdate(todo)"
      class="text-lg rounded-sm text-center relative px-4 py-2"
      :class="
        !todo.completed
          ? 'bg-gradient-to-r from-green-600 to-green-500'
          : 'bg-gradient-to-r from-gray-500 to-gray-600 text-white'
      "
      v-for="todo in allTodos"
      :key="todo.id"
    >
      {{ todo.title }}
      <i
        @click="deleteTodo(todo.id)"
        class="fas fa-trash-alt text-sm absolute bottom-1 right-2 text-white cursor-pointer"
      ></i>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";
export default {
  created() {
    this.fetchTodos();
  },
  computed: {
    ...mapGetters(["allTodos"]),
  },
  methods: {
    ...mapActions(["fetchTodos", "deleteTodo", "updateTodo"]),
    onUpdate(todo) {
      const updTodo = {
        id: todo.id,
        title: todo.title,
        completed: !todo.completed,
      };
      this.updateTodo(updTodo);
    },
  },
};
</script>

<style></style>
