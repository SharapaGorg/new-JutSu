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
        <br/>
        <div class='logo-container' id="logo"></div>
        <br/>
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

.logo-container {
  text-align: center;
  background: none !important;
  position : relative;
  right : 30px;
}

body {
  background: #1f1f1f;
}

</style>

<script>

import * as THREE from "three/build/three.module.js"
import {GLTFLoader} from 'three/examples/jsm/loaders/GLTFLoader.js';

const WIDTH = 330;
const HEIGHT = 80;

let scene = new THREE.Scene();

function load(loader) {
  loader.load('http://192.168.1.47:8080/logo.glb', function (gltf) {
      scene.add(gltf.scene);
    },
    function (xhr) {
      console.log((xhr.loaded / xhr.total * 100) + '% loaded');
    }, function (error) {
      console.error(error);
    });
}

function addLighting() {
  let hlight = new THREE.AmbientLight(0x404040, 0);
  scene.add(hlight);
  let directionalLight = new THREE.DirectionalLight(0xffffff, 0);
  directionalLight.position.set(0, 1, 0);
  directionalLight.castShadow = true;
  scene.add(directionalLight);
  let light = new THREE.PointLight(0xc4c4c4, 1);
  light.position.set(0, 300, 500);
  scene.add(light);
  let light2 = new THREE.PointLight(0xc4c4c4, 1);
  light2.position.set(500, 100, 0);
  scene.add(light2);
  let light3 = new THREE.PointLight(0xc4c4c4, 1);
  light3.position.set(0, 100, -500);
  scene.add(light3);
  let light4 = new THREE.PointLight(0xc4c4c4, 1);
  light4.position.set(-500, 300, 500);
  scene.add(light4);
}

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
      },
      camera: null,
      scene: new THREE.Scene(),
      renderer: new THREE.WebGLRenderer(
        {antialias: true}
      )
    }
  },
  methods: {},
  mounted() {
    let container = document.getElementById("logo");

    scene.background = new THREE.Color(0x1f1f1f);
    const camera = new THREE.PerspectiveCamera(8, WIDTH / HEIGHT, 0.1, 2000);
    const renderer = new THREE.WebGLRenderer();
    renderer.setSize(WIDTH, HEIGHT);

    // align canvas center
    renderer.domElement.style.display = "block";
    renderer.domElement.style.margin = "auto";

    container.appendChild(renderer.domElement);

    addLighting();

    const loader = new GLTFLoader();

    load(loader);

    renderer.outputEncoding = THREE.sRGBEncoding;
    camera.position.y = 1;
    camera.position.z = 5;

    scene.rotation.x -= 0.1;

    // render logo
    const animate = function () {
      requestAnimationFrame(animate);

      renderer.render(scene, camera);
    };
    animate();
  },

  components: {}
}

</script>

