<template>
  <div class="global-button">
    <v-btn large color="primary" type="submit" @click="onClick"><slot>Button</slot></v-btn>
  </div>
</template>
<script>
export default {
  name: 'global-button',
  props: {
    onClick: {
      required: true
    }
  } 
}
</script>
<style lang="scss">

</style>
