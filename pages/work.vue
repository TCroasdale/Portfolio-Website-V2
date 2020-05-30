<template>
  <div class="container">
    <h1>My Work</h1>
    <div class="projects-container">
        <ProjectCard v-for="project in allProjects" :key="project.path"></ProjectCard>
    </div>
  </div>
</template>

<script>
import ProjectCard from '~/components/ProjectCard.vue'

export default {
  components: {
      ProjectCard
  },
  asyncData({ app }) {
    return {
      allProjects: app.$markdown.content,
      projectsFrontMatter: app.$markdown.loadData()
    }
  },
  data: () => {
    return {
      aboutTab: false,
      workTab: false,
      contactTab: false,
      pageContent: null
    }
  },
  created() {
  }

}
</script>

<style lang="scss">
  @import "~/assets/colours.scss";

  .container {
    display: block;
    width: 80%;
    margin: 3rem auto;
    min-height: 100vh;
    // background-color: $colour-primary-0;
    padding: 1rem 5px;
  }

  .container h1 {
    background-color: $colour-primary-0;
    color: $colour-primary-1;
    width: 50%;
    min-width: 250px;
    margin: 1rem auto;
    padding: 2px 2rem;
    font-size: 2rem;
    border-radius: 2rem;
    border: 1rem;
  }

  .projects-container {
      display: flex;
      flex-flow: row wrap;
  }

</style>
