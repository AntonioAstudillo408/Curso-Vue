<script setup>
import { ref } from 'vue';
import BlogPost from './components/BlogPost.vue';
import PaginatePost from './components/PaginatePost.vue';
import LoadingSpinner from './components/LoadingSpinner.vue';

const posts = ref([]);
const favorito = ref('');
const url = 'https://jsonplaceholder.typicode.com/posts';
const postXpage = 10;
const inicio = ref(0);
const fin = ref(postXpage);
const loading = ref(true);


const cambiarFavorito = (post) =>   favorito.value = post;

fetch(url)
.then(res => res.json())
.then(data => posts.value = data)
.finally(() => {
    setTimeout(() => {
        loading.value = false;
    },2000);
});

const next = () => {
    inicio.value = inicio.value + postXpage;
    fin.value = fin.value + postXpage;
}

const previous = () => {
    inicio.value = inicio.value - postXpage;
    fin.value = fin.value - postXpage; 
}





</script>

<template>
    <h1>App Padre</h1>
    <h2>Mi Post Favorito: {{ favorito }}</h2>

    <div v-if="loading">
        <LoadingSpinner  ></LoadingSpinner>
    </div>
    <div v-else>
        <div class="container">

            <PaginatePost  @siguiente="next"  @anterior="previous" :inicio="inicio" :fin="fin" :tamano="posts.length" />


            <BlogPost
                v-for="post in posts.slice(inicio,fin)"
                :key="post.id"      
                :title="post.title"
                :body="post.body"
                :id="post.id"
                @cambiarFavoritoNombre="cambiarFavorito"
            >
            </BlogPost>
            <hr>
        </div>
    </div>
</template>

<style>


</style>