<script setup>
    defineProps(['title' , 'author']);


//    defineProps({
//     title:String,
//     id:nunmbe
//    })
</script>




<template>
    <div class="card">
        <div class="card-body">
            <h5 class="card-title">
                {{ title }}
            </h5>
            <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Doloremque dicta quod exercitationem distinctio tempora nisi pariatur aut? Reprehenderit maxime magni repellendus. Odit eius fugiat tempora quisquam doloribus quasi, provident blanditiis!</p>
       
            <blockquote>
                Author - {{ author }}
            </blockquote>

            <button @click="$emit('cambiarFavorito', title)" 
            class="btn btn-outline-dark">Favorito</button>
       </div>
    </div>
</template>