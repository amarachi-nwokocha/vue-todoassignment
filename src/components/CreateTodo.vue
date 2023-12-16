<script>
export default {
data(){
  return {
      inputValue: "", // To store the value from the input field
      myArray: [
      { text: 'Example todo 1', editing: false }
      ], // The array to store the values
    };
},
methods:{
  addTodo() { 
    // Method for adding a new item in the list
    if(this.inputValue === '' ){
      alert("Please enter a task")
    }else{
      this.myArray.push({text: this.inputValue, editing: false})
      console.log(this.myArray);
    this.inputValue = '';
    }
    },
}

}
</script>

<template>
  <div class="flex justify-center align-middle bg-gray-400 ">
     <input type="text" v-model="inputValue" @keyup.enter="CreateTodo" class=""/>
     <button @click="CreateTodo">Add</button>
   </div>
</template>


<style>

</style>