<template>
  <div id="header">
    <div class="title">
      <h1>Tom Croasdale</h1>
      <h3>Software Developer</h3>
    </div>
    <nav ref="navbar">
      <div v-bind:style="highlightStyle" ref="nav-highlight" id="nav-highlight"></div>
      <ul>
        <li ref="Home-tab" v-on:mouseover="tab='Home-tab'" v-on:mouseout="tab=currentTab">Home</li>
        <li ref="About-tab" v-on:mouseover="tab='About-tab'" v-on:mouseout="tab=currentTab">About</li>
        <li ref="Work-tab" v-on:mouseover="tab='Work-tab'" v-on:mouseout="tab=currentTab">My Work</li>
        <li ref="Contact-tab" v-on:mouseover="tab='Contact-tab'" v-on:mouseout="tab=currentTab">Contact</li>
      </ul>
    </nav>
  </div>
</template>

<script>
module.exports = {
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