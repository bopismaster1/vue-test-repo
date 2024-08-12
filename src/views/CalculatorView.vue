<script setup>
import { ref } from "vue";
import CalculatorButton from "../components/CalculatorButton.vue";
const input = ref("");
const total = ref(0);
const insertInput = (e) => {

  if (String(input.value).length <= 9) {
    input.value != 0 ? (input.value = input.value + `${e}`) : (input.value = e);
  }
};

const calculate = (e) => {
    console.log(e);
    
  switch (e) {
    case "+":
      total.value = total.value + input.value;
      break;
    case "-":
      total.value = total.value - input.value;
      break;
    case "*":
      total.value = total.value * input.value;
      break;
    case "/":
      total.value = total.value / input.value;
      break;
    default:
      console.log(e);
  }
};
</script>

<template>
  <div
    class="h-screen bg-red-400 md:flex md:justify-center md:items-center p-5"
  >
    <div
      class="bg-black md:w-[400px] md:h-[550px] rounded-lg p-3 flex-rows mt-20"
    >
      <div class="flex justify-center">
        <span class="text-white text-3xl justify-self-center"
          >The Calculator</span
        >
      </div>
      <input
        class="block w-full p-2 rounded-lg mt-[50px] text-right text-2xl"
        type="text"
        readonly
        placeholder="0"
        v-model="input"
      />

      <div class="grid grid-cols-4 gap-4 text-white mt-4">
        <CalculatorButton color="gray" content="%" @my-event="insertInput" />
        <CalculatorButton color="gray" content="CE" @my-event="insertInput" />
        <CalculatorButton color="gray" content="C" @my-event="insertInput" />
        <CalculatorButton color="gray" content="remove" icon="divide" />
      </div>
      <div class="grid grid-cols-4 gap-4 text-white mt-4">
        <CalculatorButton color="gray" content="7" @my-event="insertInput" />
        <CalculatorButton color="gray" content="8" @my-event="insertInput" />
        <CalculatorButton color="gray" content="9" @my-event="insertInput" />
        <CalculatorButton color="gray" content="remove" icon="xmark" />
      </div>
      <div class="grid grid-cols-4 gap-4 text-white mt-4">
        <CalculatorButton color="gray" content="4" @my-event="insertInput" />
        <CalculatorButton color="gray" content="5" @my-event="insertInput" />
        <CalculatorButton color="gray" content="6" @my-event="insertInput" />
        <CalculatorButton color="gray" content="remove" icon="minus" />
      </div>
      <div class="grid grid-cols-4 gap-4 text-white mt-4">
        <CalculatorButton color="gray" content="3" @my-event="insertInput" />
        <CalculatorButton color="gray" content="2" @my-event="insertInput" />
        <CalculatorButton color="gray" content="1" @my-event="insertInput" />
        <CalculatorButton color="gray" content="remove" icon="plus" @my-event="calculate"/>
      </div>
      <div class="grid grid-cols-4 gap-4 text-white mt-4">
        <CalculatorButton color="gray" content="00" @my-event="insertInput" />
        <CalculatorButton color="gray" content="0" @my-event="insertInput" />
        <CalculatorButton color="orange" content="remove" icon="equals" />
        <CalculatorButton color="red" content="remove" icon="delete-left" />
      </div>
    </div>
  </div>
</template>
