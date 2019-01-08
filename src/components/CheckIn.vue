<template>
  <div>
    <div>
      <label>緯度</label>
      <input type="text" v-model="lat">
      <label>経度</label>
      <input type="text" v-model="lon">
    </div>
    <input type="text" v-model="comment">
    <button class="checkin btn btn-primary">チェックイン!</button>
  </div>
</template>

<script>
export default {
  name: "CheckIn",
  methods: {}
};
</script>

<style>
</style>
