<template>
  <div>
    <nav
      class="navbar header has-shadow is-primary"
      role="navigation"
      aria-label="main navigation"
    >

      <div style = "position : relative; top: 5px !important">
        <b-dropdown :triggers="['hover']" v-for="dropdown in dropdowns" :key = "dropdown.id">
          <template #trigger="{ active }">
            <b-button
              :label = dropdown.name
              type="is-primary"
              icon-right="apps" />
          </template>

          <b-dropdown-item v-for = "item in dropdown.values" :key = "item">{{ item }}</b-dropdown-item>

        </b-dropdown>
      </div>
    </nav>

    <section class="main-content columns" style = "background-color : #1f1f1f !important;">
      <div class="container column is-10 min-h-screen">
        <nuxt/>
      </div>

    </section>
  </div>
</template>

<script>
export default {
  name: 'HomePage',
  data() {
    return {
      prefix : "col-start-",
      dropdowns: {
        types: {
          id : 0,
          name : "ТИПЫ",
          values: ["Ниндзюцу", "Тайдзюцу", "Гендзюцу"]
        },
        water: {
          id : 1,
          name : "ВОДА",
          values : ["Дерево", "Лёд", "Шторм", "Сталь", "Пар"]
        },
        lighting: {
          id : 2,
          name : "МОЛНИЯ",
          values : ["Шторм", "Скорость", "Магнетизм", "Взрыв"]
        },
        earth: {
          id : 3,
          name : "ЗЕМЛЯ",
          values : ["Дерево", "Кристалл", "Лава", "Пыль", "Тьма", "Сталь", "Магнетизм"]
        },
        wind: {
          id : 4,
          name : "ВЕТЕР",
          values : ["Лёд", "Пыль", "Скорость", "Жар", "Тайфун"]
        },
        fire : {
          id : 5,
          name : "ОГОНЬ",
          values : ["Лава", "Пыль", "Тьма", "Сталь", "Пламя", "Жар", "Взрыв", "Пар"]
        },
        chakra: {
          id : 6,
          name : "ЧАКРА",
          values : []
        }
      }
    }
  },

  components: {}
}
</script>
