<template>
  <section class="container">

      <div class="md-layout overview">
        <div class="md-layout-item md-xsmall-size-100 md-medium-size-50 md-large-size-33 cv tile">
          <AboutMe/>
        </div>
        <div v-for="(project) in projects" :key="project.id" class="md-layout-item md-xsmall-size-100 md-medium-size-50 md-large-size-33 project tile">

          <md-card>
            <md-card-media-cover md-text-scrim>
              <md-card-media md-ratio="1:1">
                <img :src="'http://dev.ushmorov.de/' + project.image.path" alt="Skyscraper">
              </md-card-media>

              <md-card-area>
                <md-card-header>
                  <span class="md-title">{{ project.title }}</span>
                  <div class="md-subhead" v-html="project.summary"></div>
                  <ul class="technics">
                    <li v-for="(tag) in project.tags" :key="tag"><md-chip>{{ tag }}</md-chip></li>
                  </ul>
                </md-card-header>

                <md-card-actions>
                  <md-button><a :href="project.link">zum Projekt</a></md-button>
                </md-card-actions>
              </md-card-area>
            </md-card-media-cover>
          </md-card>

        </div>
      </div>
    <FooterComponent/>
  </section>
</template>

<script>
  import FooterComponent from '~/components/Footer.vue'
  import AboutMe from '~/components/AboutMe.vue'

  export default {
    components: {
      FooterComponent,
      AboutMe
    },
    data() {
      return {
        projects: []
      }
    },
    created() {
      this.fetchProjects()
    },
    methods: {
      async fetchProjects() {
        await this.$axios.$get('http://dev.ushmorov.de/backend/api/collections/get/Projects')
          .then((response) => {

            console.log('PROJECTS', response.entries)

            this.projects = response.entries
          })
      }
    }
  }
</script>

<style>
</style>
