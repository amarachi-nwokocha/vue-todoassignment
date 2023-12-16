<script>

export default {
  data() {
    return {
      inputValue: "", // To store the value from the input field
      myArray: [
      
      ], // The array to store the values
    };
  },
  methods: {
    CreateTodo(){
console.log(this.inputValue);
if (this.inputValue == ""){
  alert("Please enter a task");
  } else {
    this.myArray.push({title:this.inputValue, editing:false, id:Math.random(), isCompleted: false})
    this.inputValue = ""
    console.log(this.myArray);
    }
    },
    deleteItem(item){
      console.log(item);
      const index = this.myArray.indexOf(item);
      if (index > -1) {
        this.myArray.splice(index, 1);
        }
        },
        // edit the todo
        editItem(item) {
          item.editing = true
          console.log(item.editing);
         let val= prompt("please enter new todo",item.title)
          console.log(val);
        if(val !== item.title){
          item.title=val;
        }  
        item.editing= false    
        console.log(item.editing);                               
          },
         //completed todo
         handleDone(item) {
           item.isCompleted = !item.isCompleted
           console.log( item.isCompleted);
          },
},
}
</script>



<template>
  <div class="gid place-content-center py-4 px-4">
   <div class="flex justify-center align-middle">
     <input type="text" v-model="inputValue" @keyup.enter="CreateTodo" class="
     
     "/>
     <button @click="CreateTodo">Add</button>
   </div>
 <div>
   <ul class="mt-8 grid place-content-center  max-w-screen-lg mx-auto">
     <li v-for="(todo) in myArray" :key="todo.id" class="flex justify-around align-middle gap-2">
       <!-- loop through todo myArray -->
       <input type="checkbox"  name="" id="" @click="handleDone(todo)">
       <p  :class="{ 'completed': todo.completed }">{{ todo.title }}</p>
       <font-awesome-icon icon="trash" @click="deleteItem(todo)" />
       <font-awesome-icon icon="pen-to-square" @click="editItem(todo)" />
   </li>
   </ul>
 </div>
  </div>
 </template>
<style>
.completed {
  text-decoration: line-through;
  color: gray;
  /* Additional styles for completed todos */
}

</style>