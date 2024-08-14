<script setup>
import { onMounted,ref } from 'vue';
import axios from 'axios';
const DeckId=ref("");
const DeckData=ref([]);
const playerCard = ref([]);
const ShufflleCards= async ()=>{
    let cardData= await axios.get('https://www.deckofcardsapi.com/api/deck/new/shuffle/?deck_count=1');
    console.log(cardData);
    DeckId.value=cardData.data.deck_id
    DeckData.value=cardData.data
    
}
const start = async()=>{
    let drawData= await axios.get(`https://www.deckofcardsapi.com/api/deck/${DeckData.value.deck_id}/draw/?count=2`);
    playerCard.value=drawData.data.cards
    DeckData.value=drawData.data;
    
}
</script>

<template>
    <div class="bg-green-500 h-screen flex flex-col justify-between">
        <div class="bg-red-500 h-[150px]  w-full flex justify-center">
            <img class="h-[200px] mt-2" src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/9e/Playing_card_diamond_9.svg/819px-Playing_card_diamond_9.svg.png" alt="">
            <img class="h-[200px] mt-2" src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/9e/Playing_card_diamond_9.svg/819px-Playing_card_diamond_9.svg.png" alt="">
        </div>
        <div class="bg-blue-500 h-[200px] w-full flex justify-center">

            <img class="h-[200px] mt-[-55px]" src="https://png.pngtree.com/png-vector/20231023/ourmid/pngtree-a-solitary-blue-deck-of-playing-cards-against-a-png-image_10172619.png" alt="">
            <button class=" text-xl m-2" @click="ShufflleCards">New Game</button>
            <button class=" text-xl m-2" @click="start">Start</button>
        </div>
        <div class="bg-red-500 h-[150px]  w-full flex justify-center">
            <img class="h-[200px] mt-[-55px]" :src="`${ playerCard.length>0? playerCard[0].image: wala }`" alt="">
            <img class="h-[200px] mt-[-55px]" :src="`${ playerCard.length>0? playerCard[1].image: wala }`" alt="">
        </div>
    </div>
</template>