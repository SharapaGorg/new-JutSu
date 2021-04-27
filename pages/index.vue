<template>
  <section class="section">
    <div class = "box primary_back" style = "position: relative; z-index : 1">

      <search :list = anime_list placeholder="e.g. Тёмный дворецкий"></search>
<br/>
      <b-switch v-model="isSwitchedCustom"
                true-value="Войти на сайт"
                false-value="Шакалить">
        {{ isSwitchedCustom }}
      </b-switch>
    </div>
    <div class = "box secondary_back" style = "position: relative; bottom : 35px; z-index : 0">
      OK
    </div>
  </section>
</template>

<style>

.primary_back {
  background : #515b3b !important;
  color : white
}

.secondary_back {
  background : #1f1f1f !important;
}

</style>

<script>

import Search from '~/components/search'

export default {
  name: 'HomePage',
  data() {
    return {
      selected : '',
      isSwitchedCustom: 'Шакалить',
      anime_list : ['Моя геройская академия', 'Магическая битва', 'Атака Титанов', 'Тёмный дворецкий'].sort()
    }
  },
  components: {
    Search
  }
}
</script>
