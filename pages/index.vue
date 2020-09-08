<template>
  <div>
    <v-parallax dark src="/background.jpg" class="parallax">
      <v-row align="center" justify="center">
        <v-col class="text-center" cols="12">
          <h1 class="title-text">
            Good {{ periodOfDay }}!
            <br>Welcome to my blog!
          </h1>
          <h3> Here I share my discoverings and experiences as a Web Dev.  I hope we can learn together! </h3>
        </v-col>
      </v-row>
    </v-parallax>
  </div>
</template>

<script>
export default {

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

<style scoped>
  .title-text {
    text-shadow: 1px 1px wheat;
    color: black;
  }
  .parallax {
    min-height: 100vh;
  }
</style>
