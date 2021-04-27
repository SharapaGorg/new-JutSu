<template>
  <section class="section">

    <div class = "box primary_back">
<!--      <b-field>-->
<!--        <b-autocomplete-->
<!--          class = "primary_back"-->
<!--          rounded-->
<!--          :data="anime_list"-->
<!--          placeholder="e.g. Моя геройская академия"-->
<!--          icon="magnify"-->
<!--          clearable-->
<!--          @select="option => this.selected = option">-->
<!--          <template #empty>No results found</template>-->
<!--        </b-autocomplete>-->
<!--      </b-field>-->

      <search></search>

    </div>

  </section>
</template>

<style>

.primary_back {
  background-color : #515b3b !important;
  background : #515b3b !important;
  color : white !impotant;
}

</style>

<script>

import Search from '~/components/search'

export default {
  name: 'HomePage',
  data() {
    return {
      selected : '',
      anime_list : ['Моя геройская академия', 'Магическая битва', 'Атака Титанов'].sort()
    }
  },
  components: {
    Search
  }
}
</script>
