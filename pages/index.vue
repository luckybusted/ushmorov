<template>
  <section class="container">
    <div>
      <div class="md-layout overview">
        <div class="md-layout-item md-medium-size-50 cv tile">
          <h1 class="title">
            Ivan Ushmorov
          </h1>
         <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Cumque enim exercitationem facilis fugiat hic in ipsum magni, natus voluptates?</p>
        </div>
        <div v-for="(project) in projects" :key="project.id" class="md-layout-item md-medium-size-50 md-large-size-33 project tile">
          <h3 class="title">{{ project.title }}</h3>
          <ul class="technics">
            <li v-for="(tag) in project.tags" :key="tag"><md-chip>{{ tag }}</md-chip></li>
          </ul>
          <div class="project-bg" :style="{'background-image': `url(http://dev.ushmorov.de/${project.image.path})`}"></div>
        </div>
      </div>
    </div>
    <FooterComponent/>
  </section>
</template>

<script>
  import FooterComponent from '~/components/Footer.vue'

  export default {
    components: {
      FooterComponent
    },
    data() {
      return {
        projects: []
      }
    },
    created() {
      this.fetchSomething()
    },
    methods: {
      async fetchSomething() {
        await this.$axios.$get('http://dev.ushmorov.de/backend/api/collections/get/Projects')
          .then((response) => {
            this.projects = response.entries
          })
      }
    }
  }
</script>

<style>
</style>
