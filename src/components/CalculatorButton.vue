<script setup>
import { defineProps,defineEmits } from 'vue';

const props=defineProps({
    color:String,
    content:String,
    icon:{
        type:String,
        default:"NA"
    }
})
const emits = defineEmits(['myEvent', 'calculateEvent'])
</script>

<template>
    <button :class="`flex-none h-[40px] rounded-lg bg-${props.color}-500`" v-if="icon !='NA'" @click="$emit('calculateEvent',icon)"> <fa :icon="icon"/></button>
    <button :class="`flex-none h-[40px] rounded-lg bg-${props.color}-500`" v-else @click="$emit('myEvent',content)"> {{ content }}</button>
</template>