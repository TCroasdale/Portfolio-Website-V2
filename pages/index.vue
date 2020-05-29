<template>
  <div class="container">
    <Header />
    <div>
      <ThreeDViewer />
    </div>
    <script src="https://kit.fontawesome.com/af2b26fd07.js" crossorigin="anonymous"></script>
  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'
import Header from '~/components/Header.vue'
import ThreeDViewer from '~/components/3DViewer.vue'

export default {
  components: {
    Logo,
    Header,
    ThreeDViewer
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
}
</style>
