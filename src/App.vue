<template>
  <div id="app">
    <NavBar/>
    <DiskContainer/>
  </div>
</template>

<script>
import NavBar from './components/NavBar.vue';
import DiskContainer from './components/DiskContainer.vue';


export default {
  name: 'App',
  components: {
    NavBar,
    DiskContainer,
  }
}
</script>

<style lang="scss">
@import './assets/style/main.css';

</style>
