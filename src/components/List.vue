<template>
  <div>
    <table class="table">
      <thead>
        <tr>
          <th>時間</th>
          <th>緯度</th>
          <th>経度</th>
          <th>コメント</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in items" :key="index">
          <td>{{item.created_at }}</td>
          <td>{{ item.lat }}</td>
          <td>{{ item.lon }}</td>
          <td>{{ item.comment }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "List",
  props: ["items"]
};
</script>

<style>
</style>
