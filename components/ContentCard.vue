<template>
  <v-container

    xl-8
    lg-6
    md-8
    sm-12
    xs-12
  >
    <div class="text-right" @click="$emit('close')">
      <v-icon>mdi-close</v-icon>
    </div>
    <div v-for="post in content" :key="post.slug">
      <v-divider class="mb-5 mt-5" />
      <nuxt-link :to="post.path">
        <h2 @click="$emit('close')">
          {{ post.title }}
        </h2>
      </nuxt-link>
      <div class="overline">
        <v-icon small>
          mdi-information-variant
        </v-icon>
        {{ post.strapline }}
      </div>
    </div>
  </v-container>
</template>

<script>
export default {
  data () {
    return {
      content: []
    }
  },
  async mounted () {
    const content = await this.$content('articles').fetch()
    this.content = content
  }
}
</script>
