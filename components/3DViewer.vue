<template>
  <div class="canvas-parent" ref="canvas-parent">
  </div>
</template>

<script>
const THREE = require('three')
const GLTF = require("../node_modules/three/examples/jsm/loaders/GLTFLoader")

export default {
  data: function () {
    return {
      scene: null,
      camera: null,
      renderer: null,
      loader: null,
      size: {
        w: 0,
        H: 0
      }
    }
  },
  methods: {
    animate: function () {
      requestAnimationFrame(this.animate)
      this.renderer.render(this.scene, this.camera)
    }
  },
  mounted: function () {
    this.scene = new THREE.Scene();
    this.size.w = this.$refs['canvas-parent'].offsetWidth
    this.size.h = this.$refs['canvas-parent'].offsetHeight
    this.camera = new THREE.PerspectiveCamera(40, this.size.w / this.size.h, 0.1, 1000)

    this.renderer = new THREE.WebGLRenderer({antialias: true, alpha: true})
    this.renderer.setSize(this.size.w, this.size.h)
    this.$refs['canvas-parent'].appendChild(this.renderer.domElement)
    this.renderer.setClearColor(0xA3B8C2)

    this.animate()

    this.loader = new GLTF.GLTFLoader()
    this.loader.load('/models/FullScene.glb', (gltf) => {
      console.log("gltf", gltf)
      this.scene.add(gltf.scene)
      this.camera.position.z = 40
      this.camera.position.y = 50
      console.log(this.camera)
    }, (xhr) => {
      console.log((xhr.loaded / xhr.total * 100) + '% loaded')
    }, (err) => {
      console.log("err", err)
    })
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