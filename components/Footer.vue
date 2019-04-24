<template>
  <v-layout px-3>

      <v-flex xs6  class="copy">
        Ivan Ushmorov &copy; {{year}} - Made with <a href="https://getcockpit.com/">getcockpit.com</a>, <a
        href="https://nuxtjs.org">NUXTJS</a> and ❤️.
      </v-flex>

      <v-flex xs6 text-xs-right class="imprint">
        <nuxt-link to="/imprint">Impressum</nuxt-link>
      </v-flex>

  </v-layout>
</template>

<script>
  export default {
    name: 'FooterComponent',
    data(){
      return {
       year: new Date().getFullYear()
      }
    }
  }
</script>

<style scoped>

</style>
