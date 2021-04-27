<template>
  <div>
    <b-field>

      <b-input icon="magnify" v-model="selected" rounded>

      </b-input>

      <!--    <b-autocomplete-->
      <!--      class="primary_back"-->
      <!--      rounded-->
      <!--      :data="inputCheck"-->
      <!--      placeholder="e.g. Моя геройская академия"-->
      <!--      icon="magnify"-->
      <!--      clearable-->
      <!--      @select="option => this.selected = option">-->
      <!--      <template #empty>No results found</template>-->
      <!--    </b-autocomplete>-->
    </b-field>

    <div v-if = "selected !== ''" style = "background-color : white; padding : 8px" class = "rounded-l-3xl">
      <ul v-for="anime in inputCheck" :key=anime>{{ anime }}</ul>
    </div>

  </div>
</template>

<script>

export default {
  data() {
    return {
      selected: '',
      anime_list: ['Моя геройская академия', 'Магическая битва', 'Атака Титанов']
    }
  },
  computed: {
    inputCheck() {
      let temp_array = []

      for (let elem in this.anime_list) {
        if (this.anime_list[elem].toLowerCase().includes(this.selected.toLowerCase()) && this.selected !== '') {
          temp_array.push(this.anime_list[elem]);
        }
      }
      if (temp_array.length !== 0) return temp_array
      else return ['У меня такого не имеется :(']
    }
  }
}

</script>
