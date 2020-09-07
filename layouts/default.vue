<template>
  <v-app>
    <v-navigation-drawer app class="aside-background">
      <side-container />
    </v-navigation-drawer>
    <v-main class="content" dark>
      <nuxt />
    </v-main>
  </v-app>
</template>

<style scoped>
    .aside-background {
      background-color: lightblue;
      color: black;
    }
    .content {
      min-height: 100vh;
    }
</style>
