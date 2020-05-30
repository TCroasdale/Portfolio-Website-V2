<template>
  <div class="container">
    <component :is="pageContent"></component>
  </div>
</template>

<script>
export default {
  asyncData({ app }) {
    return {
      // allBlogPosts: app.$markdown.content,
      // blogPostFrontMatter: app.$markdown.loadData()
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
    // this.pageContent = () => this.$markdown.loadContent()
  }
  

}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto+Mono&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Open+Sans:ital@1&display=swap'); 

.dnone {
    display: none !important;
}

h1, h2, h3, h4, h5, h6, .heading {
  font-family: 'Open Sans'
}

p, a, li, .text {
  font-family: 'Roboto Mono'
}

.container {
  margin: 0 auto;
  min-height: 100vh;
}
</style>
