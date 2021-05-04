<template>
  <div style="position: relative; z-index: 2">
    <nav
      class="navbar header has-shadow is-primary"
      role="navigation"
      aria-label="main navigation"
    >
      <div style="position : relative; top: 5px !important" class="pc-only">
        <b-dropdown :triggers="['hover']" v-for="dropdown in dropdowns" :key="dropdown.id">
          <template #trigger="{ active }">
            <b-button
              :label=dropdown.name
              type="is-primary"
              icon-right="apps"/>
          </template>
          <b-dropdown-item v-for="item in dropdown.values" :key="item">{{ item }}</b-dropdown-item>
        </b-dropdown>
      </div>
    </nav>

    <section class="main-content columns content-container">
      <div class="container column is-6 min-h-screen">
        <br/><br/><br/><br/><br/>
        <nuxt/>
      </div>
    </section>
  </div>
</template>

<style>

@media screen and (max-width: 1025px) {
  .pc-only {
    display: none
  }

  .mobile-only {
    display: block;
  }
}

@media screen and (max-width: 275px) {
  .pc-only {
    display: block;
  }

  .mobile-only {
    display: none
  }
}

.content-container {
  background: url(../assets/background_main.dark.jpg) no-repeat top, center;
}

body {
  background: #1f1f1f;
}

</style>

<script>

export default {
  name: 'HomePage',
  data() {
    return {
      dropdowns: {
        types: {
          id: 0,
          name: "ТИПЫ",
          values: ["Ниндзюцу", "Тайдзюцу", "Гендзюцу"]
        },
        water: {
          id: 1,
          name: "ВОДА",
          values: ["Дерево", "Лёд", "Шторм", "Сталь", "Пар"]
        },
        lighting: {
          id: 2,
          name: "МОЛНИЯ",
          values: ["Шторм", "Скорость", "Магнетизм", "Взрыв"]
        },
        earth: {
          id: 3,
          name: "ЗЕМЛЯ",
          values: ["Дерево", "Кристалл", "Лава", "Пыль", "Тьма", "Сталь", "Магнетизм"]
        },
        wind: {
          id: 4,
          name: "ВЕТЕР",
          values: ["Лёд", "Пыль", "Скорость", "Жар", "Тайфун"]
        },
        fire: {
          id: 5,
          name: "ОГОНЬ",
          values: ["Лава", "Пыль", "Тьма", "Сталь", "Пламя", "Жар", "Взрыв", "Пар"]
        },
        chakra: {
          id: 6,
          name: "ЧАКРА",
          values: []
        }
      }
    }
  },

  components: {}
}

import * as THREE from "three/build/three.module.js"
import {GLTFLoader} from 'three/examples/jsm/loaders/GLTFLoader.js';
// import {DRACOLoader} from 'three/examples/jsm/loaders/DRACOLoader.js';

const scene = new THREE.Scene();
scene.background = new THREE.Color(0xdddddd );
const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 2000);

const renderer = new THREE.WebGLRenderer({antialias:true});
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);

let hlight = new THREE.AmbientLight (0x404040,100);
scene.add(hlight);
let directionalLight = new THREE.DirectionalLight(0xffffff,100);
directionalLight.position.set(0,1,0);
directionalLight.castShadow = true;
scene.add(directionalLight);
let light = new THREE.PointLight(0xc4c4c4,10);
light.position.set(0,300,500);
scene.add(light);
let light2 = new THREE.PointLight(0xc4c4c4,10);
light2.position.set(500,100,0);
scene.add(light2);
let light3 = new THREE.PointLight(0xc4c4c4,10);
light3.position.set(0,100,-500);
scene.add(light3);
let light4 = new THREE.PointLight(0xc4c4c4,10);
light4.position.set(-500,300,500);
scene.add(light4);

// const geometry = new THREE.BoxGeometry();
// const material = new THREE.MeshBasicMaterial( { color: 0x00ff00 } );
// const cube = new THREE.Mesh( geometry, material );
// scene.add( cube );
const loader = new GLTFLoader();
//http://192.168.1.47:8080/room.glb
loader.load('http://192.168.1.47:8080/room.glb', function (gltf) {

    scene.add(gltf.scene);
    console.log("Scene adding completed [+]");
    console.log(gltf.scene.children[0]);

    console.log(gltf.animations); // Array<THREE.AnimationClip>
    console.log(gltf.scene); // THREE.Group
    console.log(gltf.scenes); // Array<THREE.Group>
    console.log(gltf.cameras); // Array<THREE.Camera>
    console.log(gltf.asset); // Object

  },
  function (xhr) {

    console.log((xhr.loaded / xhr.total * 100) + '% loaded');

  }, function (error) {

    console.error(error);

  });
renderer.outputEncoding = THREE.sRGBEncoding;
camera.position.x = 0;
camera.position.y = 100;
camera.position.z = 1000;

const animate = function () {
  requestAnimationFrame(animate);

  scene.rotation.y += 0.05;

  renderer.render(scene, camera);
};

animate();

</script>

