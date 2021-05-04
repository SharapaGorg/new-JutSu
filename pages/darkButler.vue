<template>

  <section class="section">
    <center>
      <h1 class="title" style="color : #bee6c3">Тёмный дворецкий</h1>
    </center>

  </section>

</template>

<!--<script>-->

<!--import * as THREE from "three/build/three.module.js"-->
<!--import {GLTFLoader} from 'three/examples/jsm/loaders/GLTFLoader.js';-->

<!--export default {-->
<!--  name: 'HomePage',-->
<!--  data() {-->
<!--    return {-->
<!--      camera: null,-->
<!--      scene: new THREE.Scene(),-->
<!--      renderer: new THREE.WebGLRenderer(-->
<!--        {antialias: true}-->
<!--      ),-->
<!--      model: null,-->
<!--      container: null,-->
<!--      document: null,-->
<!--      loader: new GLTFLoader()-->
<!--    }-->
<!--  },-->
<!--  methods: {-->
<!--    init() {-->
<!--      this.scene.background = new THREE.Color(0x1f1f1f);-->
<!--      this.camera = new THREE.PerspectiveCamera(100, this.container.clientWidth / this.container.clientHeight, 0.1, 2000);-->

<!--      this.renderer.setSize(this.container.clientWidth, this.container.clientHeight);-->
<!--      document.body.appendChild(this.renderer.domElement);-->

<!--      // lighting to make ability of seeing-->
<!--      let hlight, directionalLight, light, light2, light3, light4;-->

<!--      hlight = new THREE.AmbientLight(0x404040, 100);-->
<!--      this.scene.add(hlight);-->
<!--      directionalLight = new THREE.DirectionalLight(0xffffff, 100);-->
<!--      directionalLight.position.set(0, 1, 0);-->
<!--      directionalLight.castShadow = true;-->
<!--      this.scene.add(directionalLight);-->
<!--      light = new THREE.PointLight(0xc4c4c4, 10);-->
<!--      light.position.set(0, 300, 500);-->
<!--      this.scene.add(light);-->
<!--      light2 = new THREE.PointLight(0xc4c4c4, 10);-->
<!--      light2.position.set(500, 100, 0);-->
<!--      this.scene.add(light2);-->
<!--      light3 = new THREE.PointLight(0xc4c4c4, 10);-->
<!--      light3.position.set(0, 100, -500);-->
<!--      this.scene.add(light3);-->
<!--      light4 = new THREE.PointLight(0xc4c4c4, 10);-->
<!--      light4.position.set(-500, 300, 500);-->
<!--      this.scene.add(light4);-->


<!--      // load 3d logo model-->
<!--      this.loader.load("http://http://192.168.1.47:8080/logo.glb",-->
<!--        function (gltf) {-->
<!--          this.scene.add(gltf.scene);-->
<!--        },-->
<!--        function (xhr) {-->
<!--          console.log((xhr.loaded / xhr.total * 100) + '% loaded');-->
<!--        },-->
<!--        function (error) {-->

<!--          console.error(error);-->

<!--        });-->

<!--      this.renderer.outputEncoding = THREE.sRGBEncoding;-->

<!--      this.camera.position.x = 0;-->
<!--      this.camera.position.y = 0;-->
<!--      this.camera.position.z = 40;-->
<!--    },-->
<!--    animate() {-->
<!--      // render-->

<!--      requestAnimationFrame(this.animate);-->

<!--      this.scene.rotation.y += 0.05;-->
<!--      this.renderer.render(this.scene, this.camera);-->
<!--    }-->
<!--  },-->
<!--  mounted() {-->
<!--    this.container = document.getElementById("logo");-->

<!--    this.init();-->
<!--    this.animate();-->
<!--  },-->

<!--  components: {}-->
<!--}-->

<!--</script>-->


<!--<script>-->

<!--import * as THREE from "three/build/three.module.js"-->
<!--import {GLTFLoader} from 'three/examples/jsm/loaders/GLTFLoader.js';-->

<!--export default {-->
<!--  mounted() {-->
<!--    let container = document.getElementById("logo");-->

<!--    const scene = new THREE.Scene();-->
<!--    scene.background = new THREE.Color(0x1f1f1f);-->
<!--    const camera = new THREE.PerspectiveCamera(10, 400 / 100, 0.1, 2000);-->
<!--    const renderer = new THREE.WebGLRenderer();-->
<!--    renderer.setSize(400, 100);-->
<!--    container.appendChild(renderer.domElement);-->
<!--    let hlight = new THREE.AmbientLight(0x404040, 100);-->
<!--    scene.add(hlight);-->
<!--    let directionalLight = new THREE.DirectionalLight(0xffffff, 100);-->
<!--    directionalLight.position.set(0, 1, 0);-->
<!--    directionalLight.castShadow = true;-->
<!--    scene.add(directionalLight);-->
<!--    let light = new THREE.PointLight(0xc4c4c4, 10);-->
<!--    light.position.set(0, 300, 500);-->
<!--    scene.add(light);-->
<!--    let light2 = new THREE.PointLight(0xc4c4c4, 10);-->
<!--    light2.position.set(500, 100, 0);-->
<!--    scene.add(light2);-->
<!--    let light3 = new THREE.PointLight(0xc4c4c4, 10);-->
<!--    light3.position.set(0, 100, -500);-->
<!--    scene.add(light3);-->
<!--    let light4 = new THREE.PointLight(0xc4c4c4, 10);-->
<!--    light4.position.set(-500, 300, 500);-->
<!--    scene.add(light4);-->
<!--// const geometry = new THREE.BoxGeometry();-->
<!--// const material = new THREE.MeshBasicMaterial( { color: 0x00ff00 } );-->
<!--// const cube = new THREE.Mesh( geometry, material );-->
<!--// scene.add( cube );-->
<!--    const loader = new GLTFLoader();-->
<!--//http://192.168.1.47:8080/room.glb-->
<!--    loader.load('http://192.168.1.47:8080/logo.glb', function (gltf) {-->
<!--        scene.add(gltf.scene);-->
<!--        console.log("Scene adding completed [+]");-->
<!--        console.log(gltf.scene.children[0]);-->
<!--        console.log(gltf.animations); // Array<THREE.AnimationClip>-->
<!--        console.log(gltf.scene); // THREE.Group-->
<!--        console.log(gltf.scenes); // Array<THREE.Group>-->
<!--        console.log(gltf.cameras); // Array<THREE.Camera>-->
<!--        console.log(gltf.asset); // Object-->
<!--      },-->
<!--      function (xhr) {-->
<!--        console.log((xhr.loaded / xhr.total * 100) + '% loaded');-->
<!--      }, function (error) {-->
<!--        console.error(error);-->
<!--      });-->
<!--    renderer.outputEncoding = THREE.sRGBEncoding;-->
<!--    camera.position.x = 0;-->
<!--    camera.position.y = 0;-->
<!--    camera.position.z = 10;-->

<!--    // let direction, addCounter;-->

<!--    // direction = true;-->
<!--    // addCounter = 0;-->

<!--    const animate = function () {-->
<!--      requestAnimationFrame(animate);-->

<!--      // if (addCounter === 20) {-->
<!--      //   direction = !direction;-->
<!--      //   addCounter = 0;-->
<!--      // }-->
<!--      //-->
<!--      // direction ? scene.position.y += 0.025 : scene.position.y -= 0.025;-->
<!--      //-->
<!--      // addCounter++-->
<!--      // scene.rotation.y += 0.05;-->

<!--      renderer.render(scene, camera);-->
<!--    };-->
<!--    animate();-->
<!--  }-->
<!--}-->

<!--</script>-->
