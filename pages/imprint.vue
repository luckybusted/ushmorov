<template>
  <section class="container">
    <div v-html="imprint.content"></div>
  </section>
</template>

<script>
  import FooterComponent from '~/components/Footer.vue'

  export default {
    name: 'imprint',
    data() {
      return {
        imprint: {}
      }
    },
    components: {
      FooterComponent
    },
    created() {
      this.fetchImprint()
    },
    methods: {
      async fetchImprint() {
        await this.$axios.$get('http://dev.ushmorov.de/backend/api/singletons/get/imprint')
          .then((response) => {
            console.log(response)
            this.imprint = response
          })
      }
    }
  }
</script>

<style scoped>

</style>
