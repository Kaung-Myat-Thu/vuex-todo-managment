<template>
  <h3 class="font-bold text-xl pt-2">Add Todo</h3>
  <div>
    <form class="flex mt-2" @submit.prevent="onSubmit">
      <input
        type="text"
        v-model="title"
        class="px-4 py-2 rounded-l-md flex-[5]"
        placeholder="Add Todo..."
      />
      <input
        type="submit"
        class="bg-green-500 px-4 py-2 rounded-r-md flex-1 text-white cursor-pointer hover:bg-gradient-to-tr from-green-500 to-green-600"
        value="Submit"
      />
    </form>
  </div>
</template>

<script>
import { mapActions } from "vuex";
export default {
  data() {
    return {
      title: "",
    };
  },
  methods: {
    ...mapActions(["addTodo"]),
    onSubmit() {
      this.title = this.title.trim();
      if (this.title == "") {
        return;
      }
      this.addTodo(this.title);
      this.title = "";
    },
  },
};
</script>
