<template>
  <div id="app">
    <HeaderComponent/>
    <MainComponent/>
  </div>
</template>

<script>
// import axios from 'axios';

import HeaderComponent from './components/HeaderComponent.vue';
import MainComponent from './components/MainComponent.vue'


export default {
  name: 'App',
  components: {
    HeaderComponent,
    MainComponent,

}
}
</script>

<style lang="scss">
@import '@/assets/styles/style.scss';

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  
}
</style>
