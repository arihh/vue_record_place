<template>
  <div id="app" class="container">
    <List :items="places"/>
  </div>
</template>

<script>
import store from "./store";
import List from "./components/List.vue";

export default {
  name: "app",
  components: {
    List
  },
  data: () => store.state
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
