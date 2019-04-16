<template>
  <div>
    <h1 class="title">
      {{about.title}}
    </h1>
    <div v-html="about.summary"></div>
    <div class="social">
      <md-chip v-for="(social) in about.sociallinks" :key="social.value.name"><a :href="social.value.link">{{ social.value.name }}</a></md-chip>
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
