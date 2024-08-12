<script setup>
defineProps(
    {
        taskList:array,
    }
)
</script>

<template>
        <li class="bg-white p-2 rounded-md mt-2" v-for="(task,index) in taskList" :key="task">{{ task }} <button @click="removeTask(index)" class="text-red-400 float-end font-bold">x</button></li>
</template>