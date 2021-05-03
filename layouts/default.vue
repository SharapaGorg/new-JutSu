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

    <!-- :style="{'background-image': 'url(' + require('../assets/background_main.dark.jpg') + ')' }" -->

    <section class="main-content columns content-container"
             >
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
      contentContainer: {
        backgroundRepeat: "no-repeat",
        background: "url(../assets/background_main.dark.jpg)"
      },
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
</script>
