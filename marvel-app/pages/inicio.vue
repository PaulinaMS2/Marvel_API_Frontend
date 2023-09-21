<template>
    <div>
        <h1>Esto es solo un inicio</h1>
    </div>
    
</template>

<script setup>

import axios from "axios";

const personajes = ref([]);
const public_key = "721c2ab27468962af01883df292c40f8";
const hash = "20d5be52b1e2a81038b72aef26378bf0";

const cargar_personajes = async () => {
    const url = `https://gateway.marvel.com:443/v1/public/characters?limit=100&ts=1&apikey=${public_key}&hash=${hash}`;
    const { data } = await axios.get(url);
    personajes.value = data;
    console.log(data);
};
cargar_personajes();

</script>