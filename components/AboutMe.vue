<template>
  <div>
    <h1 class="title mb-3">
      {{about.title}}
    </h1>
    <div v-html="about.summary"></div>
    <div v-if="about.sociallinks" class="social">
      <v-btn fab small dark color="#006567" :href="about.sociallinks[1].value.link">
          <img width="50%" src="~assets/icons/xing.svg">
      </v-btn>
      <v-btn fab small dark color="#1DA1F2" :href="about.sociallinks[0].value.link">
        <img width="50%" src="~assets/icons/twitter.svg">
      </v-btn>
      <v-btn fab small dark color="#0077B5" :href="about.sociallinks[2].value.link">
        <img width="50%" src="~assets/icons/linkedin.svg">
      </v-btn>
    </div>
  </div>
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
        await this.$axios.$get('http://dev.ushmorov.de/backend/api/singletons/get/aboutme')
          .then((response) => {
            this.about = response
          })
      }
    }
  }
</script>

<style scoped>

</style>
