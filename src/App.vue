<template>
  <div id="app" class="container">
    <Place/>
  </div>
</template>

<script>
import Place from "./components/Place.vue";

export default {
  name: "app",
  components: {
    Place
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
