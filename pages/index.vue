<template>
  <div>
    <v-card-title>Good {{ periodOfDay }}! Welcome to my blog!</v-card-title>
    <v-card-subtitle>
      Below you can read some of the posts I have written on my personal blog. Please, if you have any suggestions or ideas, you can <a href="mailto:viniciusarre@gmail.com">contact me</a>! I'd love to hear from you!
    </v-card-subtitle>
    <v-card-text v-for="post in content" :key="post.slug">
      <v-divider />
      <br>
      <nuxt-link :to="post.path">
        <h2>{{ post.title }}</h2>
      </nuxt-link>
      <v-subheader>
        <v-icon small>
          mdi-information-variant
        </v-icon>
        {{ post.strapline }}
      </v-subheader>
    </v-card-text>
  </div>
</template>

<script>
export default {
  async asyncData ({ $content }) {
    const content = await $content('articles').fetch()
    return { content }
  },
  computed: {
    periodOfDay () {
      const hour = new Date().getHours()
      if (hour > 5 && hour < 12) {
        return 'Morning'
      } else if (hour >= 12 && hour < 18) {
        return 'Afternoon'
      }
      return 'Evening'
    }
  }
}
</script>
