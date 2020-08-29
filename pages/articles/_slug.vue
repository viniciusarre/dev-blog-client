<template>
  <v-container xl-10 sm-12 md-12 xs-12 lg-8>
    <nuxt-content :document="doc" />
  </v-container>
</template>

<script>
export default {
  async asyncData ({ $content, params }) {
    const docString = '/articles/' + params.slug || 'index'
    const doc = await $content(docString).fetch()
    // const [doc] = docs
    return { doc }
  }
}
</script>
