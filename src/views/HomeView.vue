<script setup>
import {ref, onMounted} from 'vue';
import NavBarVue from '../components/NavBar.vue';
import Tasklists from '../components/Tasklists.vue';
var taskList= ref([
  'Fix Bed',
  'Make Coffee'
]);
let taskName=ref("")
const addTask =()=>{
console.log("inside function",taskName.value);

taskList.value.push(taskName.value);
taskName=ref("");
}
const removeTask =(index)=>{
console.log(index);
taskList.value.splice(index,1);

}

</script>

<template>
   <div class="bg-red-400 h-screen flex items-center justify-center">
    <div class="bg-[#181A18]  w-80 min-h-80  rounded-lg grid grid-cols-1 p-2">
      <div class=" flex justify-center">

        <p class="text-white  self-center">ToDo List</p>
      </div>
      <br>
      <div class="">

        <input type="text" placeholder="Enter ToDo Here" class="block w-full rounded-md p-2" v-model="taskName">
        <button class="bg-red-400 p-2 rounded-md mt-2 block w-full text-white" @click="addTask">Add Task</button>
      </div>
      
      <ul >
        <li class="bg-white p-2 rounded-md mt-2" v-for="(task,index) in taskList" :key="index">{{ task }} <button @click="removeTask(index)" class="text-red-400 float-end font-bold">x</button></li>
      </ul>
      
    </div>
    </div>
</template>
