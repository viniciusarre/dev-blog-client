<template>
  <div class="mt-10">
    <v-row class="justify-center">
      <v-img src="/logo.png" class="hidden-sm-and-down" height="auto" max-width="200" position="center center" />
      <v-img class="hidden-md-and-up" src="/logo.png" height="auto" max-width="150" position="center center" />
    </v-row>
    <div class="py-xl-10 py-sm-1">
      <h2 class="text-center hidden-sm-and-down">
        Vinícius Arré's Web Development blog
      </h2>
      <h2 class="text-center hidden-md-and-up mt-1">
        Vinícius' Blog
      </h2>
    </div>
    <v-list v-for="item in menuItems" :key="item.title" light>
      <v-list-item class="pl-lg-5" :to="item.url">
        <v-list-item-icon>
          <v-icon class="nav-list">
            {{ item.icon }}
          </v-icon>
        </v-list-item-icon>
        <v-list-item-content>
          <v-list-item-title>
            {{ item.title }}
          </v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </div>
</template>

<script>
export default {
  data () {
    return {
      menuItems: [
        {
          title: 'Home',
          url: '/',
          icon: 'mdi-home'
        },
        {
          title: 'Content',
          url: '/content',
          icon: 'mdi-book-open-outline'
        }
      ]
    }
  }
}
</script>
