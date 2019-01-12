<template>
  <v-card class="tip-calculator">
    <input-bill
      placeHolder="Total bill"
      v-model.number="$v.bill.$model"
    />
    <p class="error" v-if="!$v.bill.required">*required</p>
    <dropdown-tip-amount 
      :tipAmounts="tipRates" 
      v-model="selectedTip"
    />
    <global-button class="tip-calculator__cta" :onClick="handleSplit">Split bill</global-button>
    <global-button class="tip-calculator__cta" :onClick="handleCalculation">Calculate bill</global-button>
    <div class="tip-calculator__display">
      <p class="tip-calculator__display__tip">Tip: {{ this.tipAmount }}</p>
      <p class="tip-calculator__display__total-cost">Total: {{ this.totalCost }}</p>
    </div>  
  </v-card>  
</template>
<script>
import InputBill from '../components/input-bill'
import DropdownTipAmount from '../components/dropdown-tip-amount'
import GlobalButton from '../components/global-button'

import { required } from 'vuelidate/lib/validators'

export default {
  name: 'tip-calculator',
  components: {
    InputBill,
    DropdownTipAmount,
    GlobalButton
  },
  validations: {
    bill: {
      required,
    }
  },
  data() {
    return {
      bill: '',
      tipRates: [
        0.12,
        0.18,
        0.20
      ],
      selectedTip: 0.12,
      totalCost: '',
      tipAmount: ''
    }
  },
  methods: {
    /**
     * function that will split the bill evenly amount all guest
     * 
     * @returns {number}
     */
    handleSplit() {

    },
    /**
     * calculates the total cost of dinner + gratuity
     * 
     * @returns {number}
     */
    handleCalculation () {
      this.displayTipAmount(this.bill, this.selectedTip)
      this.displayTotalCost(this.bill, this.selectedTip)
    },
    /**
     * displays gratuity in dollars
     * 
     * @return {number}
     */
    displayTipAmount(bill, tip) {
      this.tipAmount = `$${parseFloat(tip * bill).toFixed(2)}`
      
      return this.tipAmount
    },
    /**
     * calculates total cost of dinner
     * 
     * @return {number}
     */
    displayTotalCost(bill, tip) {
      let cost = parseFloat(bill + (tip * bill)).toFixed(2)

      this.totalCost = `$${cost}`
      
      return this.totalCost
    }
  }
}
</script>
<style lang="scss">
.error {
  color: white;
}
.tip-calculator {
  margin: 30px auto;
  max-width: 600px;
  &__cta {
    display: inline;
  }
}
</style>
