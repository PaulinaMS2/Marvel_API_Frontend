<template>
  <v-card>
    <v-layout>

      <v-app-bar class="appbar" color=#2d355e>
        <v-app-bar-nav-icon variant="prominent" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      
          <v-img src="../public/imagenAppBar.png" max-height="70" 
          ></v-img>
          
        

      </v-app-bar>

      <v-navigation-drawer v-model="drawer" location="down" temporary max-height="70" color="gray">
      
        <NuxtLink to="/inicio">
          <v-list-item><v-icon icon="mdi-view-dashboard" style="color: #2d355e;"/>    Inicio    </v-list-item>
        </NuxtLink>
        <NuxtLink to="/personajes">
          <v-list-item><v-icon icon="mdi-weather-hurricane" style="color: #2d355e;"/>  Personajes Marvel  </v-list-item>
        </NuxtLink>
      </v-navigation-drawer>
      <v-main >
        <!-- slot: Carga el contenido de la página (pages/..) -->
        <slot />
      </v-main>
    </v-layout>
  </v-card>
</template>
<style scoped>
  a {
  text-decoration: none; /* Quitar subrayado */
  color: black;
  }

  .appbar{
    overflow: hidden !important;
  }
</style>

<script>
export default {
  data: () => ({
    drawer: false,
  }),

  watch: {
    group() {
      this.drawer = false
    },
  },
}
</script>