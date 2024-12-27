<script setup>
import { computed } from 'vue';
const emit = defineEmits(['siguiente' , 'anterior'])
const props = defineProps(['inicio' , 'fin' , 'tamano']);
const siguiente = () => { 
    emit('siguiente');
 }
const anterior = () => {
    emit('anterior');

}


const botonInicio = computed(()=> {
    return props.inicio === 0;
});


const botonFinal = computed(()=>{
    return props.fin === props.tamano;
});


</script>



<template>
    <div class="btn-group mt-3 mb-3" role="group" aria-label="Basic example">
        <button :disabled="botonInicio" type="button" @click="anterior" class="btn btn-primary">Previous</button>
        <button :disabled="botonFinal" type="button" @click="siguiente" class="btn btn-primary">Next</button>
    </div>
</template> 