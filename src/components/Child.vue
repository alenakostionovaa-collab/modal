<script setup>
import { ref } from 'vue';

console.log('sssss')
const  count = ref(0);
const add =()=> {
    count.value++;
}

</script>

<template>
    <button @click="add">count</button>
    <div @click="add">dddd</div>
    {{count}}
    <div>s</div>

</template>