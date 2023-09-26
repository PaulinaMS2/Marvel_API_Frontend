<template >
    <v-container class="container">
      <v-row>
        <v-col v-for="personaje in personajes" :key="personaje.id" cols="12"
          sm="6"
          md="4"
          lg="3">
          <v-card class="personaje-card" >
          <v-img class="personaje-img" :src="personaje.thumbnail.path + '.' + personaje.thumbnail.extension"></v-img>
          <v-card-title>{{ personaje.name }}</v-card-title>
          <v-card-actions>
              <v-btn class="btn" variant="outlined" @click="viewMore()">
                  Detalles 
              </v-btn>
          </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  
  </template>
  
  <style>
  
  .container {
    align-items: justify !important;
    justify-content: justify !important;
    flex-direction: column !important;
   }
  
  .personaje-card {
      background-color: whitesmoke;
      border-color: black;
      color: black;
      
  }
  
  .personaje-img {
      width: 300px;
      height: 300px;
  }
  </style>
  
  
  
<script setup>
  
  import axios from "axios";
  
  const personajes = ref([]);
  const public_key = "721c2ab27468962af01883df292c40f8";
  const hash = "20d5be52b1e2a81038b72aef26378bf0";
  
  const cargar_personajes = async () => {
      const url = `https://gateway.marvel.com:443/v1/public/characters?limit=100&ts=1&apikey=${public_key}&hash=${hash}`;
      const { data } = await axios.get(url);
     
      // Descartar los personajes que no tienen imagen
      const personajesConImagen = data.data.results.filter(personaje => {
        return personaje.thumbnail.path != "http://i.annihil.us/u/prod/marvel/i/mg/b/40/image_not_available"
      });
  
      personajes.value = personajesConImagen;
      console.log(personajesConImagen)
  }
  cargar_personajes();
  
</script>