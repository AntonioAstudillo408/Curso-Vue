
<script setup>

import {ref , computed} from 'vue';

const nombre = 'Antonio Astudillo';
const arrayColores = ['blue' , 'red' , 'yellow'];
const activo = true;
let color =  ref('green');
// const arrayFrutas = ['Manzana' , 'Platano' , 'Sandía' , 'Fresa' , 'Uvas' , 'Pera' , 'Chocolate'];
let numero = ref(0);


function sumar(){
  numero.value++;
}

function restar(){
  numero.value--;
}



const comprobarValorColor = computed(() => {
    if(numero.value === 0){
      color.value = 'black';
    }else if(numero.value < 0){
      color.value = 'red';
    }else{
      color.value = 'green';
    }

    return color.value;
})



function resetear(){
  numero.value = 0;
}


const arrayFrutas = [
    {
      name:'Manzana',
      price: "$1.00",
      description: "Una manzana",
    },
    {
      name: "Pera",
      price: "$2.00",
      description: "Una pera",
    },
    {
      name:"Naranja",
      price: "$3.00",
      description: "Una naranja",
    },
];

const objetoFruta = {
   name:"Manzana",
   price: "$1.00",
   description: "Una manzana",
   id:1,
}


/**
 * Propiedades computadas 
 */

 const classCounter = computed(() => {
     if(numero.value === 0) {
      return 'black';
     }

     if(numero.value > 0){
      return 'green';
     }


     if(numero.value < 0){
      return 'red';
     }
 });



 /**
  * Ejercicio 2 
  */

  const numeros = ref([]);

  function agregar(){

    if(!numeros.value.includes((numero.value))){
      numeros.value.push(numero.value);
    }

  }


  const bloquearBoton = computed(() => {
        return numeros.value.includes(numero.value);
  });



</script>


<template>
  <h1>Hola Vue js</h1>
  <p>Mi nombre es: {{ nombre.toUpperCase() }} </p>
  <p :style="`color:${arrayColores[2]}`">Soy azul</p>
  <p>{{ arrayColores }}</p>
  

  <ol>
    <li v-for="fruta in arrayFrutas" :key="fruta.name">{{ fruta.name }} - {{ fruta.price }} - {{ fruta.description }}</li>
  </ol>

  <hr>

  <ol>
    <li v-for="objeto in objetoFruta">
      {{ objeto }}
    </li>
  </ol>


  <!-- <ul>
    <li :key="index" v-for="(fruta,index) of arrayFrutas">{{ fruta }}</li>
  </ul> -->

  
  <p v-if="activo"  >Estoy activo</p>
  <p v-else>Estoy inactivo</p>
  

  <hr>
  <h1>Bloque de codigo para trabajar con la reactividad</h1>
  <button class="btn btn-primary"  v-on:click="sumar">+</button>
  <button class="btn btn-danger" v-on:click="restar">-</button>
  <button class="btn btn-warning" v-on:click="resetear">Reset</button>
  <button class="btn btn-info" v-on:click="agregar" :disabled="bloquearBoton" >Agregar</button>
  <p>Número: <span :style="{ color: comprobarValorColor }">{{ numero }}</span>  </p>
  <p>Valor de color {{ color }}</p>

<hr>


<h1>Arreglo de numeros</h1>


<ul>
  <li v-for="numero in numeros">{{ numero }}</li>
</ul>





</template>


<style>
  h1{
    color:red;
  }
</style>