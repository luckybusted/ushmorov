<template>
  <section class="container">
    <div v-html="imprint.content"></div>
  </section>
</template>

<script>
  import FooterComponent from '~/components/Footer.vue'
  import avatar from '~/assets/images/twitter-avatar.jpg'

  export default {
    name: 'imprint',
    data() {
      return {
        imprint: {}
      }
    },
    head(){
      return {
        title: 'Imprint of Ivan Ushmorov',
        meta: [
          { hid: 'description', name: 'description', content: 'Frontend developer. Based in Munich, Germany.' },
          { hid: 'twitter-card', name: 'twitter:card', content: 'summary' },
          { hid: 'twitter-site', name: 'twitter:site', content: '@luckybusted' },
          { hid: 'twitter-image', name: 'twitter:image', content: avatar }
        ]
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
        await this.$axios.$get('https://dev.ushmorov.de/backend/api/singletons/get/imprint')
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
