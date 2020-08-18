<template>
  <Layout>
    <v-card-title primary-title>
      <h2>{{ $page.post.title }}</h2>
      <v-spacer></v-spacer>
       <div class="text-right">
         <v-subheader>
          <v-icon small style="margin-right: 0.5em">mdi-alarm</v-icon>
          {{$page.post.date}}
         </v-subheader>
      </div>
    </v-card-title>
    <v-card-text style="word-break: normal"  v-html="$page.post.content" />
  </Layout>
</template>

<page-query>
query BlogPost ($path: String!) {
  metadata {
    siteName
    siteDescription
  }
  post: blogPost (path: $path) {
    id
    title
    strapline
    date (format: "D MMMM YYYY")
    author
    content
  }
}
</page-query>

<style scoped>
  h1, h2 {
    color: #8BC34A
  }
</style>