<template>
  <div>
    <Spinner v-bind:isLoading="!isLoaded" />
    <Header ref="header"></Header>
    <div>
      <ThreeDViewer @loaded="onBGLoad"></ThreeDViewer>
    </div>
    <nuxt />
  </div>
</template>

<script>
import Vue from 'vue'
import Logo from '~/components/Logo.vue'
import Icon from '~/components/Icon.vue'
import Header from '~/components/Header.vue'
import ThreeDViewer from '~/components/3DViewer.vue'
import Spinner from '~/components/Spinner.vue'

Vue.component('Icon', Icon)

export default {
  components: {
    Logo,
    Header,
    ThreeDViewer,
    Spinner,
    Icon
  },
  data: function () {
    return {
      isLoaded: false
    }
  },
  methods: {
    onBGLoad: function (e) {
      this.isLoaded = true
    }
  },
  transition: "default"
}
</script>

<style>
html {
  font-family: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}

.button--green {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #3b8070;
  color: #3b8070;
  text-decoration: none;
  padding: 10px 30px;
}

.button--green:hover {
  color: #fff;
  background-color: #3b8070;
}

.button--grey {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #35495e;
  color: #35495e;
  text-decoration: none;
  padding: 10px 30px;
  margin-left: 15px;
}

.button--grey:hover {
  color: #fff;
  background-color: #35495e;
}


.page-enter-active,
.page-leave-active {
  transition-property: opacity;
  transition-timing-function: ease-in-out;
  transition-duration: 500ms;
}
.page-enter,
.page-leave-to {
  opacity: 0;
}
</style>
