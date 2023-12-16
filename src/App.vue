<template>
  <div class="grid place-content-center ">
    <h1 class="text-center text-purple-600 my-20 text-4xl font-bold">
      To Do App
    </h1>
    <div class="bg-gray-200 max-w-full  rounded-md">
      <TodoForm />
    </div>
  </div>
  <div></div>
</template>

<script>
import TodoForm from "./components/TodoForm.vue";
export default {
  components: { TodoForm,CreateTodo },
  name: "Todo-App",
  methods: {},
};
</script>

<style>
</style>