<template>
  <div id="header" v-bind:class="{large : isLarge }">
    <div class="title">
      <h1>Tom Croasdale</h1>
      <h3>Software Developer</h3>
    </div>
    <nav ref="navbar">
      <ul>
        <a href="#"><li ref="Home-tab" @click="currentTab='Home-tab'" @mouseover="tab='Home-tab'" @mouseout="tab=currentTab"><i class="fas fa-home"></i>Home</li></a>
        <a href="#"><li ref="About-tab" @click="currentTab='About-tab'" @mouseover="tab='About-tab'" @mouseout="tab=currentTab">About</li></a>
        <a href="#"><li ref="Work-tab" @click="currentTab='Work-tab'" @mouseover="tab='Work-tab'" @mouseout="tab=currentTab">My Work</li></a>
        <a href="#"><li ref="Contact-tab" @click="currentTab='Contact-tab'" @mouseover="tab='Contact-tab'" @mouseout="tab=currentTab">Contact</li></a>
      </ul>
      <div :style="highlightStyle" ref="nav-highlight" id="nav-highlight"></div>
    </nav>
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      tab: undefined,
      isLarge: true,
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
    },
    currentTab: function(val, oldVal) {
      this.isLarge = val == 'Home-tab'
    }
  },
  mounted: function() {
    this.tab = this.currentTab
  }
}
</script>

<style lang="scss" scoped>
  @import "~/assets/colours.scss";


  #header {
    width: 100%;
    text-align: center;
    justify-content: center;
    transition-duration: 1s;
    transition-property: width, height, transform;
    transition-timing-function: linear;
  }

  .title {
    background-color: $colour-primary-0;
    color: $colour-primary-1;
    font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
    text-align: center;

    transition-duration: 1s;
    transition-property: height, border-radius;
    transition-timing-function: linear;
  }

  #nav-highlight {
    position: relative;
    height: 4px;
    width: 20%;
    background-color: $colour-primary-0;
    transition: left 0.1s linear 0.01s;

    bottom: -1rem;
  }

  nav {
    background-color: $colour-primary-1;
    color: $colour-primary-0;
    font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
    text-align: center;

    height: 2rem;

    transition-duration: 1s;
    transition-property: height, border-radius;
    transition-timing-function: linear;
  }

  nav ul {
    margin-top: 0;
    padding: 6px 0 6px 0;
    height: 1rem;
  }

  nav ul li {
    display: inline-block;
    width: 20%;
  }

   #header.large {
     width: 50%;
     height: 12rem;
     margin: 0 0;
     border-radius: 15px;
     justify-content: center;
    //  box-shadow: 0px 0px 15px black;
     transform: translate(50%, 40vh);

    .title {
      height: 8rem;
      font-size: 1.5rem;
      border-top-left-radius: 15px;
      border-top-right-radius: 15px;
    }

    nav {
      height: 4rem;
      border-bottom-left-radius: 15px;
      border-bottom-right-radius: 15px;
    }

    nav ul {
      transform: translateY(50%);
    }

    #nav-highlight {
      height: 4px;
      bottom: -2rem;
      width: 75% * 0.25;
    }
  }

</style>