<template>
  <div class="d-flex flex-no-wrap justify-space-between">
    <div class="mt-1">
      <v-card-title class="headline">
        {{ content.title }}
      </v-card-title>
      <v-card-subtitle class="content mt-1">
        <nuxt-content :document="content" />
      </v-card-subtitle>
    </div>
    <v-avatar
      class="ma-3 mt-3"
      size="125"
      tile
    >
      <v-img class="profile-photo" :src="content.img" :alt="content.alt" />
    </v-avatar>
  </div>
</template>

<script>
export default {
  data () {
    return {
      content: {}
    }
  },
  async mounted () {
    const content = await this.$content('about').fetch()
    console.log('content >> ', content)
    this.content = content
  }
}
</script>

<style scoped>
  .profile-photo {
    border-radius: 20em;
  }
  .content {

    font-size: 15px;
  }
</style>
