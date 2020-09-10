<template>
  <v-app class="app">
    <v-app-bar class="hidden-md-and-up" dark>
      <v-app-bar-nav-icon @click="mobileNavbar = !mobileNavbar" />
    </v-app-bar>
    <!-- default navbar -->
    <v-navigation-drawer app class="aside-background hidden-sm-and-down">
      <side-container />
    </v-navigation-drawer>
    <!-- mobile navbar -->

    <v-navigation-drawer v-model="mobileNavbar" app class="mobile-background hidden-md-and-up">
      <div class="text-right mr-3 mt-5 ">
        <v-icon class="aside-text" @click="mobileNavbar = !mobileNavbar">
          mdi-close
        </v-icon>
        <side-container :mobile="true" />
      </div>
    </v-navigation-drawer>
    <v-main class="content">
      <nuxt />
    </v-main>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      mobileNavbar: false
    }
  }
}
</script>

<style>
    .aside-text {
      color: black;
    }
    .aside-background {
      background-color: lightblue !important;
      color: black;
    }
    .mobile-background {
      min-width: 100vw;
      background-color: lightblue !important;
      color: black;
    }
    .content {
      min-height: 100vh;
    }
</style>
