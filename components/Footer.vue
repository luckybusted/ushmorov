<template>
  <v-layout pa-3 footer>

      <v-flex xs9  class="copy">
        Ivan Ushmorov &copy; {{year}} - Made with <a href="https://getcockpit.com/">getcockpit.com</a>, <a
        href="https://nuxtjs.org">NUXTJS</a> and ❤️.
      </v-flex>

      <v-flex xs3 text-xs-right class="imprint">
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
