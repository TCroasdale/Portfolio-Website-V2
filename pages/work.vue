<template>
  <div class="container">
  </div>
</template>

<script>

export default {
  data: () => {
    return {
      aboutTab: false,
      workTab: true,
      contactTab: false,
    }
  },
  methods: {
    changeTab: function (e) {}
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
