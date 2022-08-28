<template>
  <div class="px-6 md:px-12 container mx-auto">
    <AddTodos />
    <FilterTodos />
    <Todos />
  </div>
</template>

<script>
import Todos from "./components/Todos.vue";
import FilterTodos from "./components/FilterTodos.vue";
import AddTodos from "./components/AddTodos.vue";
export default {
  name: "App",
  components: {
    Todos,
    AddTodos,
    FilterTodos,
  },
};
</script>
