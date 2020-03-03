<template>
  <div class="canvas-parent" ref="canvas-parent">
  </div>
</template>

<script>
var THREE = require('three')
export default {
  data: function () {
    return {
      scene: null,
      camera: null,
      renderer: null,
      size: {
        w: 0,
        H: 0
      }
    }
  },
  methods: {
    animate: function () {
      requestAnimationFrame( this.animate );
      this.renderer.render( this.scene, this.camera );
    }
  },
  mounted: function () {
    this.scene = new THREE.Scene();
    this.size.w = this.$refs['canvas-parent'].offsetWidth
    this.size.h = this.$refs['canvas-parent'].offsetHeight
    this.camera = new THREE.PerspectiveCamera( 75, this.size.w / this.size.h, 0.1, 100 );

    this.renderer = new THREE.WebGLRenderer();
    this.renderer.setSize( this.size.w, this.size.h );
    this.$refs['canvas-parent'].appendChild( this.renderer.domElement );

    let geometry = new THREE.BoxGeometry();
    let material = new THREE.MeshBasicMaterial( { color: 0x00ff00 } );
    let cube = new THREE.Mesh( geometry, material );
    this.scene.add( cube );

    this.camera.position.z = 5;

    this.animate()
  }
}
</script>
<style lang="scss" scoped>
  .canvas-parent {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    display: block;
    z-index: -1;
  }
  canvas {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
  }
</style>