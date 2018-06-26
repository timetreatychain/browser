<template>
  <div id="app_inner">
    <heador class="header"></heador>  
    <cont1></cont1>
    <footer1></footer1>
  </div>
</template>

<script>
import heador from '../base/header'
import cont1 from '../components/content'
import footer1 from "../base/footer"
export default {
  name: 'home',
  components: {
    heador,
    cont1,
    footer1 
  }
}
</script>

<style scoped>
#app_inner{
  width: 100%;
}
  .header{
    position: sticky;
    top: 0;
    z-index: 99999;
    width: 100%;
  }
</style>