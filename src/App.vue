<template>
  <div id="app">
    <v-app>
      <v-content>
        <tip-calculator></tip-calculator>
      </v-content>
    </v-app>
  </div>
</template>

<script>
import TipCalculator from './views/tip-calculator'


export default {
  name: 'app',
  components: {
    TipCalculator
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
