<script>
export default {
  data() {
    return {
      inputValue: "", // To store the value from the input field
      myArray: [], // The array to store the values
    };
  },
  methods: {
    CreateTodo() {
      console.log(this.inputValue);
      if (this.inputValue == "") {
        alert("Please enter a task");
      } else {
        this.myArray.push({
          title: this.inputValue,
          editing: false,
          id: Math.random(),
          isCompleted: false,
        });
        this.inputValue = "";
        console.log(this.myArray);
      }
    },
    deleteItem(item) {
      console.log(item);
      const index = this.myArray.indexOf(item);
      if (index > -1) {
        this.myArray.splice(index, 1);
      }
    },
    // edit the todo
    editItem(item) {
      item.editing = true;
      console.log(item.editing);
      let val = prompt("please enter new todo", item.title);
      console.log(val);
      if (val !== item.title) {
        item.title = val;
      }
      item.editing = false;
      console.log(item.editing);
    },
    //completed todo
    handleDone(item) {
      item.isCompleted = !item.isCompleted;
      console.log(item.isCompleted);
    },
  },
};
</script>



<template>
  <div class="p-4">
    <div class="flex justify-center align-middle">
      <input
        type="text"
        v-model="inputValue"
        @keyup.enter="CreateTodo"
        class="mt-4 p-2 border border-gray-300 rounded"
      />
      <button @click="CreateTodo" class="flex mt-5 bg-purple-500 px-5 rounded py-2 mx-5  text-white">Add</button>
    </div>
    <div>
      <ul class="mt-8">
        <li
          v-for="todo in myArray"
          :key="todo.id"
          class="flex items-center justify-around py-2"
        >
          
          <p :class="{ completed: todo.completed }" class="text-xl font-semibold capitalize">{{ todo.title }}</p>
          <font-awesome-icon
            icon="trash"
            class="px-3 py-1 text-red-500 text-[20px]"
            @click="deleteItem(todo)"
          />
          <font-awesome-icon
            icon="pen-to-square"
            class="px-3 py-1 text-green-500 text-[20px]"
            @click="editItem(todo)"
          />
        </li>
      </ul>
    </div>
  </div>
</template>
<style>

</style>