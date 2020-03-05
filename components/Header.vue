<template>
  <div id="header">
    <div class="title">
      <h1>Tom Croasdale</h1>
      <h3>Software Developer</h3>
    </div>
    <nav ref="navbar">
      <div :style="highlightStyle" ref="nav-highlight" id="nav-highlight"></div>
      <ul>
        <li ref="Home-tab" @click="currentTab='Home-tab'" @mouseover="tab='Home-tab'" @mouseout="tab=currentTab">Home</li>
        <li ref="About-tab" @click="currentTab='About-tab'" @mouseover="tab='About-tab'" @mouseout="tab=currentTab">About</li>
        <li ref="Work-tab" @click="currentTab='Work-tab'" @mouseover="tab='Work-tab'" @mouseout="tab=currentTab">My Work</li>
        <li ref="Contact-tab" @click="currentTab='Contact-tab'" @mouseover="tab='Contact-tab'" @mouseout="tab=currentTab">Contact</li>
      </ul>
    </nav>
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      tab: undefined,
      currentTab: 'Home-tab',
      highlightStyle: {
        left: "50px"
      }
    }
  },
  watch: {
    tab: function (val, oldVal) {
      let highlight = this.$refs['nav-highlight']
      this.highlightStyle.left = this.$refs[val].offsetLeft + 'px'
    }
  },
  mounted: function() {
    this.tab = this.currentTab
    let a = this.$refs['navbar']
    this.highlightStyle.top = a.offsetTop + a.offsetHeight - 2 + 'px'
  }
}
</script>

<style lang="scss" scoped>
  @import "~/assets/colours.scss";

  .header {
    text-align: center;
    justify-content: center;
  }

  .title {
    background-color: $colour-primary-0;
    color: $colour-primary-1;
    font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
    text-align: center;
  }

  #nav-highlight {
    position: fixed;
    height: 2px;
    width: 20%;
    background-color: $colour-primary-0;
    transition: left 0.1s linear;
    transition-delay: 0.01s;
  }

  nav {
    background-color: $colour-primary-1;
    color: $colour-primary-0;
    font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
    text-align: center;
  }

  nav ul {
    margin-top: 0;
    padding: 6px 0 6px 0;
  }

  nav ul li {
    display: inline-block;
    width: 20%;
  }

</style>