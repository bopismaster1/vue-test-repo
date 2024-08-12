<script setup>
import { ref } from 'vue';
const menuIcon = ref('bars')
const menu =()=>{
    let list=document.getElementById("navlinks");
    
    
    menuIcon.value =="bars"? (list.classList.add('top-[80px]'), list.classList.add('opacity-100'),menuIcon.value="xmark") :(list.classList.remove('top-[80px]'), list.classList.remove('opacity-100'),menuIcon.value="bars")
}
</script>
<template>
    <nav class="bg-white p-5 md:flex md:items-center md:justify-between">
        <div class="flex justify-between">
            <span class="tet-2l font-[Poppins]">
                <img src="https://seeklogo.com/images/T/tailwind-css-logo-5AD4175897-seeklogo.com.png" class="h-10 inline" alt="">
                Vue + Tailwind Project
            </span>
            <span class="text-2xl md:opacity-0">
                <fa  :icon="menuIcon" @click="menu()"/>
            </span>
        </div>  
        <ul id="navlinks" class="md:flex md:items-cennter z-[1] md:z-auto md:static absolute bg-white w-full left-0 md:w-auto md:opacity-100 opacity-0 top-[-400px] transitio ease-in duration-500">
            <li class="tet-2xl p-4"><a href="/">Todo List</a></li>
            <li class="tet-2xl p-4"><a href="/calculator">Calculator</a></li>
            <li class="tet-2xl p-4"><a href="#">Lorem</a></li>
            <li class="tet-2xl p-4"><a href="#">Ipsum</a></li>
        </ul>     
    </nav>
</template>