<template>


  <v-layout wrap class="overview">
    <v-flex xs12 md6 class="cv tile">
      <AboutMe/>
    </v-flex>
    <v-layout wrap>


      <v-flex xs12 sm6 md4 pa-3 v-for="(project) in projects" :key="project.id" class="project tile">

        <v-card>
          <!--<v-img :src="'http://dev.ushmorov.de/' + project.image.path"
                 aspect-ratio="1"/>-->


          <v-card-title primary-title>
            <span class="md-title">{{ project.title }}</span>
            <div class="md-subhead" v-html="project.summary"></div>
            <ul class="technics">
              <li v-for="(tag) in project.tags" :key="tag">
                <v-chip>{{ tag }}</v-chip>
              </li>
            </ul>
          </v-card-title>

          <v-card-actions>
            <v-btn flat><a :href="project.link">zum Projekt</a></v-btn>
          </v-card-actions>


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
