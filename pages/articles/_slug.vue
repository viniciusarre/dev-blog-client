<template>
  <v-container
    xl-8
    lg-8
    md-10
    sm-12
    xs-12
  >
    <v-card raised>
      <div class="px-2">
        <v-card-title>
          <div class="card-title">
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

        <v-card-text class="card-content">
          <nuxt-content :document="doc" limit="200" />
        </v-card-text>
      </div>
    </v-card>
  </v-container>
</template>

<script>
export default {
  data () {
    return {
      doc: {}
    }
  },
  async mounted () {
    const docString = 'articles/' + this.$route.params.slug
    const doc = await this.$content(docString).fetch()
    this.doc = doc
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
.card-title {
  font-size: 22px;
}
.card-content {
  word-break: normal;
  font-size: 15px;
}
</style>
