<template>
  <v-container
    xl-8
    lg-8
    md-10
    sm-12
    xs-12
    class="content"
  >
    <v-card raised>
      <v-card-title>
        <div class="">
          {{ doc.title }}
        </div>

        <v-spacer />
        <div class="text-right overline">
          <v-subheader>
            <v-icon small style="margin-right: 0.5em">
              mdi-calendar
            </v-icon>
            {{ formatDate(doc.date) }}
          </v-subheader>
        </div>
      </v-card-title>

      <v-card-text style="word-break: normal/">
        <nuxt-content :document="doc" />
      </v-card-text>
    </v-card>
  </v-container>
</template>

<script>
export default {
  async asyncData ({ $content, params }) {
    const docString = '/articles/' + params.slug || 'index'
    const doc = await $content(docString).fetch()
    // const [doc] = docs
    return { doc }
  },
  methods: {
    formatDate (date) {
      const d = new Date(date)
      const months = ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December']
      const month = months[d.getMonth()]
      const day = this.formatDay(d.getDate())
      return `${month}, ${day} - ${d.getFullYear()}`
    },

    formatDay (day) {
      if (day === 1) {
        return '1st'
      } else if (day === 2) {
        return '2nd'
      } else if (day === 3) {
        return '3rd'
      }
      return `${day}th`
    }
  }
}
</script>

<style scoped>
.content {
  font-size: 20px;
}
</style>
