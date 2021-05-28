<template>
  <div id="app">

    <main-comp /> 

  </div>
</template>

<script>

import MainComp from './components/MainComp.vue'

export default {
  name: 'App',
  components: {
    MainComp
    
  }
}
</script>

<style lang="scss">
#app {

};

body{
  margin:0;
  padding: 0;
  background-color: #434343;
  
}
</style>
