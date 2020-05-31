<template>
  <div class="fullscreen-bg" v-bind:class="{ hidden: !isLoading }">
    <Icon class="spinner" icon="cog" />
  </div>
</template>

<script>
import Icon from '~/components/Icon.vue'

export default {
  components: {
      Icon
  },
  props: {
      isLoading: Boolean
  }
}
</script>

<style lang="scss" scoped>
@import "~/assets/colours.scss";

.fullscreen-bg.hidden {
    transform: translateY(-100%);
    transition: transform 1s linear;
}

.fullscreen-bg {
    z-index: 100;
    position: fixed;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    display: block;
    background-color: $colour-primary-3;
    color: $colour-primary-0;
}

@keyframes spin {
    from {transform:translate(50vw, 50vh) scale(10) rotate(0deg);}
    to {transform:translate(50vw, 50vh) scale(10) rotate(360deg);}
}

.fullscreen-bg > .spinner {
    // width: 50%;
    transform: translate(50vw, 50vh) scale(10);
    animation: spin 4s infinite linear;
}
</style>
