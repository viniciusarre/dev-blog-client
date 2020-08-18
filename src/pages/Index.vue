<template>
  <Layout>
    <v-card-title>Good {{periodOfDay}}! Welcome to my blog!</v-card-title>
    <v-card-subtitle>
      Below you can read some of the posts I have written on my personal blog. Please, if you have any suggestions or ideas, you can <a href="mailto:viniciusarre@gmail.com">contact me</a>! I'd love to hear from you!
    </v-card-subtitle>
    <v-card-text v-for="post in $page.allBlogPost.edges" :key="post.node.id" >
      <v-divider />
      <br/>
      <g-link :to="post.node.path">
        <h2>{{ post.node.title }}</h2>
      </g-link>
      <v-subheader>
        <v-icon small>mdi-information-variant</v-icon>
        {{ post.node.strapline }}
      </v-subheader>
    </v-card-text>
  </Layout>
</template>

<script>
export default {
  computed: {
    periodOfDay(){
      const hour = new Date().getHours()
      if(hour > 5 && hour < 12) {
        return 'Morning'
      } else if (hour >=12 && hour < 18) {
        return "Afternoon"
      }
      return "Evening"
    }
  }
}
</script>

<page-query>
  query {
    metadata {
      siteName
      siteDescription
    }
    allBlogPost {
      totalCount
      edges {
        node {
          path
          id
          title
          strapline
          date (format: "MMM D YYYY")
          author
        }
      }
    }
  }
</page-query>