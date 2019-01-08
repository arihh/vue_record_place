<template>
  <div id="app" class="container">
    <CheckIn/>
    <List :items="places"/>
  </div>
</template>

<script>
import store from "./store";
import CheckIn from "./components/CheckIn.vue";
import List from "./components/List.vue";

export default {
  name: "app",
  components: {
    CheckIn,
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
