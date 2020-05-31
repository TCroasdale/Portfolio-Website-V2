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
      },
      bodies: [],
      clock: undefined,
      targetFPS: 30,
      scale: 3
    }
  },
  methods: {
    animate: function () {
      setTimeout(() => {
        requestAnimationFrame(this.animate)
      }, 1000 / this.targetFPS )
      this.updateBodies()

      this.camera.position.x = Math.sin(this.clock.elapsedTime * 0.25) * 25 * this.scale
      this.camera.position.z = Math.cos(this.clock.elapsedTime * 0.25) * 25 * this.scale
      this.camera.lookAt(this.bodies[this.bodies.length - 1].position)

      this.renderer.render(this.scene, this.camera)
    },
    createSolarSystem: function (num) {
      num = num == undefined ? 3 : num;
      console.log(`creating ${num} bodies`)
      let material = new THREE.MeshToonMaterial({color: 0xaaaaaa })
      let sunMaterial = new THREE.MeshToonMaterial({color: 0xffff00 })

      for (let i = 0; i < num; i ++) {

        let size = (this.scale / num)
        let geometry = new THREE.SphereGeometry(size, 8, 16 )
        let body = new THREE.Mesh(geometry, material)
        let x = (Math.random()-0.5)*2 * this.scale * 10
        let y = (Math.random()-0.5)*2 * this.scale * 10
        let z = (Math.random()-0.5)*2 * this.scale * 10
        body.position.set(x, y, z)
        body.userData = {
          vx: 0, vy: 0, vz: 0,
          m: size,
          canMove: true
        }
        this.scene.add(body)
        this.bodies.push(body)
      }

      /** Create Sun */
      let light = new THREE.PointLight(0xffffff, 1, 100)
      let size = (this.scale * 2 / num)
      let geometry = new THREE.SphereGeometry(size, 8, 16 )
      let body = new THREE.Mesh(geometry, sunMaterial)
      let x = (Math.random()-0.5)*2 * this.scale
      let y = (Math.random()-0.5)*2 * this.scale
      let z = (Math.random()-0.5)*2 * this.scale
      body.position.set(x, y, z)
      body.userData = {
        vx: 0, vy: 0, vz: 0,
        m: size,
        canMove: false
      }
      this.scene.add(body)
      body.add(light)
      this.bodies.push(body)
    },
    updateBodies: function () {
      let G = 9.81;
      let dT = this.clock.getDelta()
      for (let i=0; i < this.bodies.length; i++){
        let bodyI = this.bodies[i]
        if (bodyI.userData.canMove) {
          let sum = { x: 0, y: 0, z: 0 }
          for (let j=0; j < this.bodies.length; j++){
            if (i != j) {
              let bodyJ = this.bodies[j]
              let diff = { x: bodyJ.position.x - bodyI.position.x,
                          y: bodyJ.position.y - bodyI.position.y,
                          z: bodyJ.position.z - bodyI.position.z }

              let magSq = (diff.x * diff.x) + (diff.y * diff.y) + (diff.z * diff.z)
              if (magSq > bodyI.userData.m * this.bodies.length){
                let denominator = Math.sqrt(magSq + 0.01)
                denominator = denominator * denominator * denominator

                sum.x += (bodyJ.userData.m * diff.x) / denominator
                sum.y += (bodyJ.userData.m * diff.y) / denominator
                sum.z += (bodyJ.userData.m * diff.z) / denominator
              }
            }
          }
          let a = { x: sum.x * G, y: sum.y * G, z: sum.z * G }
          bodyI.userData.vx += a.x * dT
          bodyI.userData.vy += a.y * dT
          bodyI.userData.vz += a.z * dT
        }
      }


      for (let i=0; i < this.bodies.length; i++){
        let bodyI = this.bodies[i]
        bodyI.position.x += bodyI.userData.vx * dT
        bodyI.position.y += bodyI.userData.vy * dT
        bodyI.position.z += bodyI.userData.vz * dT
      }
    }
  },
  mounted: function () {
    this.scene = new THREE.Scene();
    this.size.w = this.$refs['canvas-parent'].offsetWidth
    this.size.h = this.$refs['canvas-parent'].offsetHeight
    this.camera = new THREE.PerspectiveCamera(40, this.size.w / this.size.h, 0.1, 1000)
    this.camera.position.z = this.scale * 50;

    this.renderer = new THREE.WebGLRenderer({antialias: true, alpha: true})
    this.renderer.setSize(this.size.w, this.size.h)
    this.$refs['canvas-parent'].appendChild(this.renderer.domElement)
    this.renderer.setClearColor(0x00000a)


    // let light = new THREE.PointLight(0xffff33, 1, 100)
    // let geometry = new THREE.SphereGeometry(this.scale * 0.1 , 8, 16 )
    // let material = new THREE.MeshToonMaterial({color: 0xffff33 })
    // let body = new THREE.Mesh(geometry, material)
    // light.position.set(0, 0, 0)
    // this.scene.add(light)
    // light.add(body)
    this.clock = new THREE.Clock()

    this.createSolarSystem(6)

    this.animate()
    this.$emit('loaded', true)
    console.log("finished loading")
    // this.loader = new GLTF.GLTFLoader()
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