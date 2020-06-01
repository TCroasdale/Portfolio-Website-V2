<template>
  <div class="container">
    <component :is="pageContent"></component>
  </div>
</template>

<script>
import Icon from '~/components/Icon.vue'

export default {
  components: {
    Icon
  },
  asyncData({ app }) {
    return {
      allBlogPosts: app.$markdown.projects,
      blogPostFrontMatter: app.$markdown.loadData()
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
    this.pageContent = () => this.$markdown.loadContent()
  }
  

}
</script>

<style lang="scss" >
  @import "~/assets/colours.scss";

  .container {
    display: block;
    width: 80%;
    margin: 3rem auto;
    // min-height: 50vh;
    // background-color: $colour-primary-0;
    padding: 1rem 5px;
  }

  .nuxt-markdown h1 {
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

  .nuxt-markdown h2 {
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

  .nuxt-markdown h4 {
    background-color: $colour-primary-1;
    color: $colour-primary-0;
    width: 100%;
    min-width: 250px;
    margin: 1rem auto;
    padding: 2px 2rem;
    font-size: 2rem;
    border-radius: 2rem;
    border: 1rem;
    text-align: center;
    text-decoration: none;

    transition: 0.1s ease-in-out;
  }

  .nuxt-markdown a {
    text-decoration: none;
  }

  .nuxt-markdown h4:hover {
    text-decoration: none;
    background-color: $colour-primary-0;
    color: $colour-primary-1;
  }

  .nuxt-markdown .small-right {
    float: right;
    font-size: 1rem;
    justify-content: center;
    margin: 0.5rem;
  }

  .nuxt-markdown h1:not(:first-child) {
    margin-top: 5rem;
  }

  .nuxt-markdown p, .nuxt-markdown > ul {
    background-color: $colour-primary-1;
    color: $colour-primary-0;
    width: 100%;
    margin: 1rem auto;
    padding: 1rem 2rem;
    font-size: 1rem;
    border-radius: 2rem;
    list-style-type: square;

    display: flex;
    flex-flow: row wrap;
    align-items: center;
    justify-content: center;
  }

  .nuxt-markdown > ul > li {
    width: 25%;
    min-width: 250px;
    margin-bottom: 1rem;
  }

  .nuxt-markdown li ul {
    margin-top: 0rem;
    padding-top: 0rem;
    display: block;
    margin: 0 auto;
  }  

</style>
