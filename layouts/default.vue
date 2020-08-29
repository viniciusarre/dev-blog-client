<template>
  <v-app dark>
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
        <nuxt-link to="/about" icon title="Info">
          <v-icon>mdi-information-outline</v-icon>
        </nuxt-link>
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
      <v-card>
        <nuxt />
      </v-card>
    </v-container>
  </v-app>
</template>
