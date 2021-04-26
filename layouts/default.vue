<template>
  <div>
    <nav
      class="navbar header has-shadow is-primary"
      role="navigation"
      aria-label="main navigation"
    >

      <div style = "position : relative; top: 5px !important">
        <b-dropdown :triggers="['hover']" v-for="dropdown in dropdowns" :key = "dropdown.name">
          <template #trigger="{ active }">
            <b-button
              :label = dropdown.name
              type="is-primary"
              icon-right="apps" />
          </template>

          <b-dropdown-item v-for = "item in dropdown.values" :key = "dropdown.name">{{ item }}</b-dropdown-item>

        </b-dropdown>
      </div>

    </nav>

    <section>
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
          id : this.prefix + "1",
          name : "ТИПЫ",
          values: ["Ниндзюцу", "Тайдзюцу", "Гендзюцу"]
        },
        water: {
          id : this.prefix + "2",
          name : "ВОДА",
          values : ["Дерево", "Лёд", "Шторм", "Сталь", "Пар"]
        },
        lighting: {
          id : this.prefix + "3",
          name : "МОЛНИЯ",
          values : ["Шторм", "Скорость", "Магнетизм", "Взрыв"]
        }
      }
    }
  },

  components: {}
}
</script>
