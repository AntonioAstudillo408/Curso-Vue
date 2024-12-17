<script setup>

import BlogPost from './components/BlogPost.vue';
import ButtonCounter from './components/ButtonCounter.vue';
import { ref } from 'vue';

const posts = ref([
    { id:1,  title:'Post 1' , author:'Ma de Jesus Jaimes'},
    { id:2,  title:'Post 2' , author:'Amairany Astudillo'},
    { id:3,  title:'Post 3' , author:'Antonio Astudillo'},
    { id:4,  title:'Post 4' , author:'Juan Astudillo'}
]);

const favorito = ref('');
const cambiarFavorito = (post) => favorito.value = post;

</script>

<template>
    <h1>App Padre</h1>
    <h2>Mi Post Favorito: {{ favorito }}</h2>
    <div class="container">
        <ButtonCounter />
        <ButtonCounter />


        <BlogPost
            v-for="post in posts"
            :key="post.id"      
            :title="post.title"
            :author="post.author" 
            @cambiarFavorito="cambiarFavorito"
        >
        </BlogPost>

        <hr>


    </div>

</template>

<style>


</style>