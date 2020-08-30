<template>
  <v-app dark>
    <v-navigation-drawer
      v-model="navDrawer"
      :right="true"
      :permanent="false"
      absolute
    >
      <v-card>
        <v-card-title class="mb-1">
          About me

          <v-spacer />
          <div class="text-right" @click="navDrawer = false">
            <v-icon>mdi-close</v-icon>
          </div>
        </v-card-title>
        <v-card-text>
          <v-img class="mb-1" src="/logo.png" />
          Hi, I'm Vinícius. A Full-Stack developer from Brazil who loves working with clients from around the world on helping them build their solutions into reality.
          In my free time, I love exploring new technologies and building small and Open Source prototypes and this blogs is a ways of documenting my journey of doing it. I am very excited about sharing my progress and discoveries with the tech community.
          Besides that, I also enjoy playing the Bass and the Guitar and reading.
        </v-card-text>
      </v-card>
    </v-navigation-drawer>
    <div>
      <v-app-bar>
        <v-btn
          icon
          to="/"
          title="Home"
        >
          <v-icon>mdi-home</v-icon>
        </v-btn>
        <v-toolbar-title>Vinícius Arré's personal blog</v-toolbar-title>
        <v-spacer />
        <span @click="navDrawer = true">
          <v-icon>mdi-information-outline</v-icon>
        </span>
      </v-app-bar>
    </div>

    <v-container
      pt-16
      xl-8
      lg-8
      md-10
      sm-12
      xs-12
    >
      <nuxt />
    </v-container>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      navDrawer: false
    }
  }
}
</script>
