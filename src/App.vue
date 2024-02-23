<script setup>
import spells from './components/spells.vue'
import controlls from './components/controlls.vue'
import mainGame from './components/mainGame.vue'

</script>

<template>
  <div class="container">   
      <controlls/>
      <mainGame/>
      <spells/>     
  </div>
</template>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
}

</style>
