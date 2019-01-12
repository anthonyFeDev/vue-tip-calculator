<template>
  <div class="dropdown-tip-amount">
    <p class="dropdown-tip-amount__dropdown">Select tip amount</p>
    <v-select class="dropdown-tip-amount__dropdown__selection" :items="tipAmounts" v-model="selectedTip" @input="event => { $emit('input', event.target.value) }">
      <option v-for="(tip, index) in tipAmounts" :key="index" :value="tip">{{ tip }}</option>
    </v-select>  
  </div>
</template>
<script>
export default {
  name: 'dropdown-tip-amount',
  props: {
    tipAmounts: {
      type: Array
    },
    value: null
  },
  data () {
    return {
      selectedTip: null
    }
  },
  methods: {
    handleSelection() {
      this.$emit.selected
    }
  },
  mounted () {
    this.selectedTip = this.value
  },

  watch: {
    value (newValue) {
      this.selectedTip = newValue
    }
  }
}
</script>
<style lang="scss">
  .dropdown-tip-amount {
    &__dropdown {
      display: inline;
      
      &__selection {
        width: 50%;
        margin: 0 auto;
      }
    }
  }
</style>

