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
          <div class="card-title text-block">
            {{ doc.title }}
          </div>

          <v-spacer />
          <div class="text-right overline">
            <v-subheader>
              <v-icon small style="margin-right: 0.5em">
                mdi-calendar
              </v-icon>
              {{ formatDate(doc.date) }}
              <v-spacer />
              <v-icon small style="margin-left: 1em; margin-right: 0.5em">
                mdi-alarm-check
              </v-icon>
              {{ readingTime }}  {{ readingTime > 1 ? 'MINS': 'MIN' }}
            </v-subheader>
          </div>
        </v-card-title>
        <v-card-text class="card-content">
          <v-alert v-if="isArchive" type="warning">
            This post was originally written in 2018, in an older version of the blog and has been republished here, since I think it can bring value to fellow developers to see the progress of my writings as well as my progress as a developer. I hope you enjoy it!
          </v-alert>
          <nuxt-content :document="doc" />
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
  computed: {
    childrenTextData () {
      const { body } = this.doc
      let txt = ''
      if (body) {
        body.children.forEach((child) => {
          // console.log('child', child.children[0].value)
          if (child && child.children && child.children.length > 0) {
            child.children.forEach((lvl2) => {
              txt = `${txt} ${lvl2.value}`
            })
          }
        })
      }
      return txt
    },
    isArchive () {
      return this.doc.archive
    },
    readingTime () {
      const wpm = 225
      const words = this.childrenTextData.trim().split(/\s+/).length
      return Math.ceil(words / wpm)
    }
  },
  mounted () {
    this.fetchDoc()
  },
  methods: {
    async fetchDoc () {
      const docString = 'articles/' + this.$route.params.slug
      const doc = await this.$content(docString).fetch()
      this.doc = doc
    },
    formatDate (date) {
      const d = new Date(date)
      const months = ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December']
      const month = months[d.getMonth()]
      const day = this.formatDay(d.getDate())
      return `${month}, ${day}`
    },

    formatDay (day) {
      if (day === 1) {
        return `${day}st`
      } else if (day === 2) {
        return `${day}nd`
      } else if (day === 3) {
        return `${day}rd`
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
