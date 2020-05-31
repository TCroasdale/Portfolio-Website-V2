<template>
  <div class="fullscreen-bg" v-bind:class="{ hidden: !isLoading }">
    <div class="y-center">
        <div class="x-center">
            <div class="spinner">
                <div class="cog-circle">
                    <div class="cog-hole"></div>
                    <div class="cog-tooth"></div>
                    <div class="cog-tooth"></div>
                    <div class="cog-tooth"></div>

                    <div class="cog-tooth"></div>
                    <div class="cog-tooth"></div>
                    <div class="cog-tooth"></div>
                </div>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
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
    from {transform: translate(-50%, -50%) rotate(0deg);}
    to {transform: translate(-50%, -50%) rotate(360deg);}
}

.fullscreen-bg .spinner {
    display: block;
    // margin: 0 auto;
    width: 175px;
    height: 175px;
    transform: translate(-50%, -50%);
    animation: spin 4s infinite linear;
}

.cog-circle {
    display: block;
    background-color: $colour-primary-0;
    width: 150px;
    height: 150px;
    border-radius: 75px;
    z-index: 11;
    transform: translate(8.3%, 8.3%);
}

.y-center {
    transform: translateY(50vh);
}

.x-center {
    transform: translateX(50vw);
}

.cog-hole {
    display: block;
    background-color: $colour-primary-3;
    width: 50px;
    height: 50px;
    border-radius: 25px;
    z-index: 11;
    transform: translate(100%, 100%);
}

.cog-tooth {
    position: absolute;
    // top: -15%;
    left: 33%;
    display: block;
    background-color: $colour-primary-0;
    width: 50px;
    height: 50px;
    z-index: 11;
}

.cog-tooth:nth-child(2) {
    transform: translateY(150%);
}

.cog-tooth:nth-child(3) {
    transform: rotate(60deg) translateY(150%);
}

.cog-tooth:nth-child(4) {
    transform: rotate(120deg) translateY(150%);
}

.cog-tooth:nth-child(5) {
    transform: translateY(-150%);
}

.cog-tooth:nth-child(6) {
    transform: rotate(60deg) translateY(-150%);
}

.cog-tooth:nth-child(7) {
    transform: rotate(120deg) translateY(-150%);
}

</style>
