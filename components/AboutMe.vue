<template>
  <div>
    <h1 class="title mb-3">
      {{about.title}}
    </h1>
    <div v-html="about.summary"></div>
    <div class="social">
      <v-btn dark round small color="blue" v-for="(social) in about.sociallinks" :key="social.value.name" :href="social.value.link">{{ social.value.name }}</v-btn>
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
