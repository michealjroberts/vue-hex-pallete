<template>
  <div id="app">
    <HexPallete/>
  </div>
</template>

<script>
import HexPallete from './components/HexPallete.vue';

export default {
  name: 'app',
  components: {
    HexPallete,
  },
};
</script>

<style lang="scss">
html, body {
  background-color: #2b2d33;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #fff;
  margin-top: 60px;
}
</style>
