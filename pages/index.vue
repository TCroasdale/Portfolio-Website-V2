<template>
  <div class="container">
    <Header ref="header" @change-tab="changeTab"></Header>
    <div>
      <ThreeDViewer></ThreeDViewer>
    </div>
    <FloatingPage v-if="aboutTab"></FloatingPage>
    <script src="https://kit.fontawesome.com/af2b26fd07.js" crossorigin="anonymous"></script>
  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'
import Header from '~/components/Header.vue'
import ThreeDViewer from '~/components/3DViewer.vue'
import FloatingPage from '~/components/FloatingPage'

export default {
  components: {
    Logo,
    Header,
    ThreeDViewer,
    FloatingPage
  },
  data: () => {
    return {
      aboutTab: false,
      workTab: false,
      contactTab: false,
    }
  },
  methods: {
    changeTab: function (e) {
      this.aboutTab = e == "About-tab"
      this.workTab = e == "Work-tab"
      this.contactTab = e == "Contact-tab"
    }
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
