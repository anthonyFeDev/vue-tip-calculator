<template>
  <div class="calculator-inputs">
    <v-text-field 
      class="calculator-inputs__bill"
      outline
      type="text" 
      :value="bill"
      :placeholder="placeHolder" 
      @input="updateBill($event.target.value)">
    </v-text-field>
  </div>
</template>
<script>
export default {
  name: 'calculator-inputs',
  props: {
    placeHolder: String,
    bill: String
  },
  data() {
    return {
    }
  },
  methods: {
    /**
     * integrating Vuetify has broken this function and app in general. 
     * I am receiving an error message (TypeError: cannot read property 'value' of undefined)
     * */ 
    updateBill(bill) {
      this.$emit('input', bill);
    }
  }
}
</script>
<style lang="scss">
.calculator-inputs {
  width: 50%;
  margin: 0 auto;
  padding-top: 20px;
}
</style>
