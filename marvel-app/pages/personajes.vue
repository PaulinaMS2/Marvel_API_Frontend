<template >
    <v-container class="container">
      <h1 class="titulo">Personajes de Marvel</h1> 
      <br>
      <v-row>
        <v-col v-for="personaje in personajes" :key="personaje.id" cols="12" sm="6" md="4" lg="3">
          <v-card class="personaje-card" elevation="8"   >
          <v-card-title class="nombreP">{{ personaje.name }}</v-card-title>
          <v-img class="personaje-img" :src="personaje.thumbnail.path + '.' + personaje.thumbnail.extension"></v-img>
          
          
          <v-card-actions>
              <v-btn class="btn" variant="outlined" block @click="openDialog(personaje);">
                  Ver personaje
              </v-btn>
          </v-card-actions>
          </v-card>
        </v-col>
        <v-card style="border-radius: 40px !important;" class="info" elevation="7">
            <v-dialog v-model="dialog" width="auto"
                style="background: none !important; border-radius: 80px !important;">
                <DescripcionP :personaje="personajeActual"></DescripcionP>
                <v-btn color="#000" class="btnSalir" block @click="dialog = false">Salir</v-btn>
            </v-dialog>
        </v-card>
      </v-row>
     
    </v-container>
  
  </template>
  
  <style>

  .btn{
    border-radius: 40px !important;
    background-color: black !important;
    color: white !important;
    border-color: white !important;
  }
  
  .btnSalir{
    background-color: #5868a4!important;
    color: white !important;
    font-weight: bold !important;
  }

  .nombreP{
    font-family:sans-serif;
    font-weight: bold !important;
    text-align: center;
  }

  .titulo{
    font-family:sans-serif;
    font-weight: bold;
    text-align: center;
  }

  .container {
    align-items: justify !important;
    justify-content: justify !important;
    flex-direction: column !important;
    overflow: auto !important;
   }
  
  .personaje-card {
      background-color: whitesmoke;
      border: 1px solid #5868a4 !important; 
      color: black;
      border-radius: 15px !important;
      
  }
  
  .personaje-img {
      width: 300px !important;
      height: 300px !important;

  }

  .info{
    border: 2px solid #d4a4a4;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.4); /* offsetX offsetY blurRadius spreadRadius color */
    width: 600px;
}

  </style>
  
  
  
<script setup>
  
  import axios from "axios";
  import DescripcionP from '~/components/DescripcionP.vue'
  
  const personajes = ref([]);
  const public_key = "721c2ab27468962af01883df292c40f8";
  const hash = "20d5be52b1e2a81038b72aef26378bf0";
  const dialog = ref(false);
  const personajeActual = ref(null);
  
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

  const openDialog = (personaje) => {
    personajeActual.value = personaje;
    dialog.value = true;
  }

  
</script>