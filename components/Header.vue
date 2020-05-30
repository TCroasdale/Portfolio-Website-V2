<template>
  <div id="header" v-bind:class="{ large : isLarge }">
    <div class="title">
      <h1>Tom Croasdale</h1>
      <h3>Software Developer</h3>
    </div>
    <nav ref="navbar">
      <ul>
        <nuxt-link to="/">
          <li ref="Home-tab" @click="currentTab='Home-tab'" @mouseover="tab='Home-tab'" @mouseout="tab=currentTab">
            <Icon icon="home"></Icon> <span class="hide-small">Home</span>
          </li>
        </nuxt-link>
        <nuxt-link to="/about">
          <li ref="About-tab" @click="currentTab='About-tab'" @mouseover="tab='About-tab'" @mouseout="tab=currentTab">
            <Icon v-bind:icon="icon"></Icon> <span class="hide-small">About</span>
          </li>
        </nuxt-link>
        <nuxt-link to="/work">
          <li ref="Work-tab" @click="currentTab='Work-tab'" @mouseover="tab='Work-tab'" @mouseout="tab=currentTab">
            <Icon icon="briefcase"></Icon> <span class="hide-small">My Work</span>
          </li>
        </nuxt-link>
        <nuxt-link to="/contact">
          <li ref="Contact-tab" @click="currentTab='Contact-tab'" @mouseover="tab='Contact-tab'" @mouseout="tab=currentTab">
            <Icon icon="comment-dots"></Icon> <span class="hide-small">Contact</span>
          </li>
        </nuxt-link>
      </ul>
      <div :style="highlightStyle" ref="nav-highlight" id="nav-highlight" class="hide-small"></div>
    </nav>
  </div>
</template>

<script>
import Icon from '~/components/Icon.vue'

export default {
  components: {
    Icon
  },
  data: () => {
    return {
      tab: undefined,
      isLarge: true,
      currentTab: 'Home-tab',
      highlightStyle: {
        left: "50px"
      },
      icons: ['user', 'user-astronaut', 'user-secret', 'user-ninja', 'user-graduate'],
      icon: "user"
    }
  },
  watch: {
    tab: function (val, oldVal) {
      let highlight = this.$refs['nav-highlight']
      this.highlightStyle.left = this.$refs[val].offsetLeft + 'px'
    },
    currentTab: function(val, oldVal) {
      this.isLarge = val == 'Home-tab'
      this.$emit('change-tab', this.currentTab)
    }
  },
  mounted: function() {
    this.tab = this.currentTab
    this.icon = this.icons[Math.floor(Math.random() * this.icons.length)]
  }
}
</script>

<style lang="scss" scoped>
  @import "~/assets/colours.scss";

  @keyframes fade {
    0% { opacity: 0 }
    100% { opacity: 100% }
  }

  #header {
    // width: 100%;
    text-align: center;
    justify-content: center;
    margin: 0 0;
    display: block;
    height: 4rem;

    /* Transition to small */
    transition: width 0.25s ease-in 0.25s, margin 0.25s ease-in 0.25s, height 0.25s ease-in 0.25s,
    transform 0.25s ease-out 0.0s;
  }

  .title {
    background-color: $colour-primary-0;
    color: $colour-primary-1;
    font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
    text-align: center;

    /* Transition to small */
    transition: width 0.25s ease-in 0.25s, margin 0.25s ease-in 0.25s, height 0.25s ease-in 0.25s,
    transform 0.25s ease-out 0.0s;
  }

  #nav-highlight {
    position: relative;
    height: 4px;
    width: 20%;
    background-color: $colour-primary-0;

    transition: left 0.1s linear 0.01s, bottom 0.25s ease-in 0.00s;
    bottom: -1rem;
  }

  nav {
    background-color: $colour-primary-1;
    color: $colour-primary-0;
    font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
    text-align: center;

    height: 2rem;

    /** Transition to large */
      transition: border-radius 0.25s ease-in 0.0s, height 0.25s ease-in 0.0s, font-size 0.25s ease-in 0.0s,
      transform 0.25s ease-out 0.25s;
  }

  nav ul {
    margin-top: 0;
    padding: 6px 0 6px 0;
    height: 1rem;

  }

  nav ul li {
    display: inline-block;
    width: 20%;
    color: $colour-primary-0
  }


  #header.large {
    // width: 75%;
    height: 12rem;
    border-radius: 15px;
    justify-content: center;
    margin: 0 12.5%;
  //  box-shadow: 0px 0px 15px black;
    transform: translateY(20vh);

    /** Transition to large */
    transition: margin 0.25s ease-in 0.0s, height 0.25s ease-in 0.0s,
    transform 0.25s ease-out 0.25s;

    .title {
      height: 8rem;
      font-size: 1.5rem;
      border-top-left-radius: 15px;
      border-top-right-radius: 15px;

      /** Transition to large */
      transition: border-radius 0.25s ease-in 0.0s, height 0.25s ease-in 0.0s, font-size 0.25s ease-in 0.0s,
      transform 0.25s ease-out 0.25s;
    }

    nav {
      height: 4rem;
      border-bottom-left-radius: 15px;
      border-bottom-right-radius: 15px;

      /** Transition to large */
      transition: border-radius 0.25s ease-in 0.0s, height 0.25s ease-in 0.0s, font-size 0.25s ease-in 0.0s,
      transform 0.25s ease-out 0.25s;
    }

    nav ul {
      transform: translateY(50%);

      /** Transition to large */
      transition: border-radius 0.25s ease-in 0.0s, height 0.25s ease-in 0.0s, font-size 0.25s ease-in 0.0s,
      transform 0.25s ease-out 0.25s;
    }

    #nav-highlight {
      height: 4px;
      bottom: -2rem;
      width: 75% * 0.25;

      /** Transition to large */
      transition: left 0.1s linear 0.01s, bottom 0.25s ease-out 0.0s;
    }
  }

   @media only screen and (max-width: 650px) {
    .hide-small {
        display: none;
    }

    #header.large .title {
      font-size: 1.25rem;
    }
  }

</style>