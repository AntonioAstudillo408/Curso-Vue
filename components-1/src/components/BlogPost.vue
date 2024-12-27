<script setup>
 const props =  defineProps(['title' , 'body' , 'id']);
 const emit = defineEmits(['cambiarFavoritoNombre']);


const actualizarFavorito = () => emit('cambiarFavoritoNombre' , props.title);


</script>




<template>
    <div class="card mb-2">
        <div class="card-body">
            <h5 class="card-title">
              {{ id }} - {{ title }}
            </h5>
            <p>{{ body }} </p>
       
            <blockquote>
                Author - Antonio Astudillo
            </blockquote>

            <button @click="actualizarFavorito" 
            class="btn btn-outline-dark">Favorito</button>
       </div>
    </div>
</template>