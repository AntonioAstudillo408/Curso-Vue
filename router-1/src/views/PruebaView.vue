<script setup>
 import axios from 'axios';
 import { ref } from 'vue';
import { RouterLink } from 'vue-router';


    const pokemons = ref([]);


    const getData = async () => {
       try {
           const {data} =  await axios.get('https://pokeapi.co/api/v2/pokemon');
           pokemons.value = data.results;
       } catch (error) {
            console.log(error);
       }
    }


    getData();


</script>

<template>
   <div class="container p-5">
        <ul class="list-group" >
            <li class="list-group-item" v-for="item in pokemons">
                <router-link :to="`/prueba/${item.name}`">{{ item.name }}</router-link>   
                
            </li>
        </ul>
   </div>
   
  
</template>