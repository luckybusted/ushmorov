<template>
  <v-app :style="{backgroundColor: body, color: textColor}">
    <v-content>
      <v-container>
        <nuxt/>
        <FooterComponent/>
      </v-container>
    </v-content>
  </v-app>
</template>
<script>
  import FooterComponent from '~/components/Footer.vue'
  import Background from '~/components/Background.vue'
  import colorable from 'colorable'
  import csscolors from 'css-color-names'

  export default {
    components: {
      FooterComponent,
      Background,
      colorable,
      csscolors
    },
    data() {
      return {
        colors: {} ,
        body: '',
        textColor: ''
      }
    },
    methods: {
      getColors() {
        this.colors = colorable(csscolors, { compact: true, threshold: 3 })
      },
      chooseColors() {

        let colLength = this.colors.length,
          colBase = this.colors[Math.floor(Math.random() * colLength)]

        this.body = colBase.hex
        this.textColor = colBase.combinations[Math.floor(Math.random() * colBase.combinations.length)].hex
        this.$vuetify.theme.success = this.textColor

      }
    },
    created() {
      this.getColors()
      this.chooseColors()
    }
  }
</script>
<style>
  html {
    font-family: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
    font-size: 16px;
    word-spacing: 1px;
    -ms-text-size-adjust: 100%;
    -webkit-text-size-adjust: 100%;
    -moz-osx-font-smoothing: grayscale;
    -webkit-font-smoothing: antialiased;
    box-sizing: border-box;
  }

  body {
    background: #fff;
  }

</style>
