<script setup>
import {ref} from 'vue';
const Pokemons = ref([]);
function loadPokemons() {
    fetch('https://pokeapi.co/api/v2/pokemon/')
        .then(function (response) {
            return response.json();
        })
        .then(function (data) {
            //console.log(data.results);

            for(let i = 0; i<data.results.length; i++){
                Pokemons.value.push(data.results[i]);
            }
        })
    }
</script>

<template>
    <button @click="loadPokemons" class="px-1 py-1 mt-3 mb-3 mx-3 bg-sky-300 rounded-lg">Cargar Pokemons</button>
    <div 
    v-for="(pok, index) in Pokemons"
    :key="index"
    class="bg-sky-200 mx-3 mb-1 py-2 px-2 w-28 rounded">
        {{ pok.name }}
    </div>
</template>