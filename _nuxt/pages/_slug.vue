<template>
  <nuxt-content />
</template>

<script>
export default {
  async asyncData ({ $content, params }) {
    const doc = await $content(params.slug || 'index').fetch()
    return { doc }
  }
}
</script>
