<template>
  <div>
    <v-parallax dark src="/background.jpg" class="parallax">
      <v-row align="center" justify="center">
        <v-col class="text-center" cols="12">
          <h1 class="title-text">
            Good {{ periodOfDay }}!
            <br>Welcome to my blog!
          </h1>
          <h3 class="subtitle">
            Here I share my discoverings and experiences as a Web Developer.
            <br>  I hope we can learn together!
          </h3>
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
    vertical-align: middle;
    text-shadow: 1px 1px wheat;
    color: black;
  }
  .subtitle {
    text-shadow: 1px 1px black;
    color: lightblue
  }
  .parallax {
    min-height: 100vh;
  }
  .background {
    background: rgb(173,216,230);
    background: linear-gradient(90deg, rgba(173,216,230,1) 49%, rgba(0,0,0,1) 100%);
    min-height: 100vh;
    width: auto;
  }
</style>
