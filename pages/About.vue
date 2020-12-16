<template>
  <v-container
    xl-5
    lg-5
    md-10
    sm-12
    xs-12
  >
    <v-card>
      <div class="d-flex flex-no-wrap justify-space-between">
        <div class="mt-1">
          <v-card-subtitle class="content mt-1">
            <v-avatar
              class="hidden-md-and-up  ma-3 mt-10"
              size="150"
              tile
            >
              <v-img class=" profile-photo" :src="content.img" :alt="content.alt" />
            </v-avatar>
            <nuxt-content :document="content" />
          </v-card-subtitle>
        </div>

        <v-avatar
          class="ma-3 mt-10 hidden-sm-and-down"
          size="150"
          tile
        >
          <v-img class=" profile-photo" :src="content.img" :alt="content.alt" />
        </v-avatar>
      </div>
    </v-card>
  </v-container>
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
