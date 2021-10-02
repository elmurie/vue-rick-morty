<template>
  <div id="app">
    <Header/>
    <Characters>
      <Character/>
    </Characters>

    
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Characters from './components/Characters.vue'
import Character from './components/Character.vue'
export default {
  name: 'App',
  components: {
    Header,
    Characters,
    Character
  }
}
</script>

<style lang="scss">
@import './assets/style/common.scss' 
</style>
