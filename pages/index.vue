<template>
  <div class="container">
    <Header />
    <div>
      <ThreeDViewer />
    </div>
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
