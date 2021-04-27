<template>
  <div>
    <b-field>
      <b-autocomplete
        rounded
        v-model="selected"
        :data="inputCheck"
        :placeholder = placeholder
        icon="magnify"
        clearable
        @select="option => this.selected = option">
        <template #empty>У меня такого не имеется :(</template>
      </b-autocomplete>
    </b-field>

  </div>
</template>

<script>

export default {
  data() {
    return {
      selected: null,
    }
  },
  props: ['list', 'placeholder'],
  computed: {
    inputCheck() {
      let temp_array = []

      for (let elem in this.list) {
        if (this.list.hasOwnProperty(elem) && this.selected !== null) {
          if (this.list[elem].toLowerCase().includes(this.selected.toLowerCase())) {
            temp_array.push(this.list[elem]);
          }
        }
      }
      return temp_array;
    }
  }
}

</script>
