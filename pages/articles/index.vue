<template>
  <v-container
    xl-8
    lg-6
    md-8
    sm-12
    xs-12
  >
    <h1 class="text-center mb-10">
      Articles
    </h1>
    <v-expansion-panels>
      <v-expansion-panel v-for="post in sortedContent" :key="post.slug">
        <v-expansion-panel-header>
          <h2 @click="$emit('close')">
            {{ post.title }}
          </h2>
          <!-- <pre>{{ post.body }}</pre> -->
          <!-- <p> {{ readingTime[post.id] }} read </p> -->
        </v-expansion-panel-header>
        <v-expansion-panel-content>
          <div class="overline">
            <v-icon small>
              mdi-information-variant
            </v-icon>
            {{ post.strapline }} <br>
            <nuxt-link :to="post.path">
              Read more
            </nuxt-link>
          </div>
        </v-expansion-panel-content>
      </v-expansion-panel>
    </v-expansion-panels>
  </v-container>
</template>

<script>

export default {
  data () {
    return {
      content: [],
      readingTime: {}
    }
  },
  computed: {
    sortedContent () {
      const { content } = this
      return content.sort((a, b) => new Date(b.date) - new Date(a.date))
    }
  },
  async mounted () {
    const content = await this.$content('articles').fetch()
    this.content = content
  }
}
</script>
