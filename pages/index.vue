<template>
</template>

<script>
export default {
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

h1, h2, h3, .heading {
  font-family: 'Open Sans'
}

p, a, li, h4, h5, h6, .text {
  font-family: 'Roboto Mono'
}
</style>
