<script setup>
 import axios from 'axios';
 import { useRoute , useRouter } from 'vue-router';
 import { ref } from 'vue';


 const route = useRoute();
 const router = useRouter();
 const pokemon = ref({});

 const back = () => {
    router.push('/prueba');
 }
 
 const getData = async () => {
       try {
           const {data} =  await axios.get(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`);
           pokemon.value = data;
       } catch (error) {
            console.log(error);
       }
    }   

 getData();

</script>


<template>
    <h1>Poke name: {{ $route.params.name }}</h1>

    <div class="container">

        <div class="card" style="width: 18rem;">
            <img v-bind:src="pokemon.sprites.front_default" class="card-img-top" alt="...">
            <div class="card-body">
                <h5 class="card-title">{{ pokemon.name }}</h5>
                <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
                <button v-on:click="back" class="btn btn-primary">regresar</button>
            </div>
        </div>

      
    </div>

</template>