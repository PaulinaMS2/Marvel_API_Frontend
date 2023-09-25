<template>
  <v-card>
    <v-layout>

      <v-app-bar class="app-bar" color="black" >
        <v-app-bar-nav-icon variant="text" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>

      </v-app-bar>

      <v-navigation-drawer v-model="drawer" location="up" temporary>
      
        <NuxtLink to="/">
          <v-list-item><v-icon icon="" style="color: black;"/> Inicio  </v-list-item>
        </NuxtLink>
        <NuxtLink to="/characters">
          <v-list-item><v-icon icon="" style="color: black;"/> Personajes Marvel </v-list-item>
        </NuxtLink>
      </v-navigation-drawer>
      <v-main >
        <!-- slot: Carga el contenido de la página (pages/..) -->
        <slot />
      </v-main>
    </v-layout>
  </v-card>
</template>


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