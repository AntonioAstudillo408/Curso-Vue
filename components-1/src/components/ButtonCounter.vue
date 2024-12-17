<script setup>

import { ref } from 'vue';

const counter = ref(0);

function increment(){
    counter.value++;
}


</script>

<template>
  <button v-on:click="increment" class="btn btn-primary">{{ counter }}</button>
</template>