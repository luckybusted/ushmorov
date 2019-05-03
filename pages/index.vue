<template>


  <v-layout wrap class="overview">
    <AboutMe/>
    <v-layout wrap>


      <v-flex xs12 sm6 pa-3 md4 v-for="(project) in projects" :key="project.id" v-if="project.active" class="project">

        <v-card height="100%">
          <!--<v-img :src="'http://dev.ushmorov.de/' + project.image.path"
                 aspect-ratio="1"/>-->


          <v-card-title primary-title>
            <h3 class="md-title">{{ project.title }}</h3>
            <div class="mb-2" v-html="project.summary"></div>
            <ul class="technics">
              <li v-for="(tag) in project.tags" :key="tag" class="mr-1">
                #{{ tag }}
              </li>
            </ul>
          </v-card-title>

          <div class="text-xs-right">
            <v-btn flat color="success" :href="project.link">zum Projekt</v-btn>
          </div>


        </v-card>

      </v-flex>
    </v-layout>
  </v-layout>
</template>

<script>
  import AboutMe from '~/components/AboutMe.vue'

  export default {
    components: {
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
        await this.$axios.$get('https://dev.ushmorov.de/backend/api/collections/get/Projects')
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
