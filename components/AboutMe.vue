<template>
  <v-layout wrap>
    <v-flex xs12 md8 pa-3>
      <h1 class="mb-3 font-weight-black text-uppercase display-4" :class="{'display-3': $vuetify.breakpoint.xs}">
        {{about.title}}
      </h1>
      <div class="headline" v-html="about.summary"></div>
    </v-flex>
    <v-flex v-if="about.sociallinks" xs12 md4 pa-3 text-md-right class="social">

        <v-btn depressed fab small dark color="#1DA1F2" :href="about.sociallinks[0].value.link">
          <img width="50%" src="~assets/icons/twitter.svg">
        </v-btn>
        <!-- <v-btn fab small dark color="#0077B5" :href="about.sociallinks[2].value.link">
          <img width="50%" src="~assets/icons/linkedin.svg">
        </v-btn> -->
        <v-btn depressed fab small dark color="#000" :href="about.sociallinks[3].value.link">
          <img width="50%" src="~assets/icons/github.svg">
        </v-btn>
        <v-btn depressed fab small dark color="#006567" :href="about.sociallinks[1].value.link">
          <img width="50%" src="~assets/icons/xing.svg">
        </v-btn>
    </v-flex>
  </v-layout>
</template>

<script>
  export default {
    name: 'AboutMe',
    data() {
      return {
        about: {}
      }
    },
    created() {
      this.fetchAboutme()
    },
    methods: {
      async fetchAboutme() {
        await this.$axios.$get('https://dev.ushmorov.de/backend/api/singletons/get/aboutme')
          .then((response) => {
            this.about = response
          })
      }
    }
  }
</script>

<style scoped>

</style>
