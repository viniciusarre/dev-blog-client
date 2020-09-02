<template>
  <v-app dark>
    <v-navigation-drawer
      v-model="contentDrawer"
      :right="false"
      :permanent="false"
      absolute
    >
      <content-card @close="contentDrawer = false" />
    </v-navigation-drawer>
    <div>
      <v-app-bar>
        <v-btn
          icon
          title="Content"
          @click="contentDrawer = true"
        >
          <v-icon>mdi-menu</v-icon>
        </v-btn>
        <v-btn
          icon
          to="/"
          title="Home"
        >
          <v-icon>mdi-home</v-icon>
        </v-btn>
        <v-toolbar-title>Vinícius Arré's personal blog</v-toolbar-title>
      </v-app-bar>
    </div>

    <nuxt />
  </v-app>
</template>

<script>
import ContentCard from '@/components/ContentCard'
export default {
  components: { ContentCard },
  data () {
    return {
      aboutDrawer: false,
      contentDrawer: false
    }
  }
}
</script>
