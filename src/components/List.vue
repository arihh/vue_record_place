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
      <button @click="loadPlaces">aaa</button>
    </table>
  </div>
</template>

<script>
export default {
  name: "List",
  props: ["items"],
  methods: {
    loadPlaces: function(e, index) {
      axios.get("http://localhost:3000/place_records.json").then(res => {
        console.log(res.data);
        this.items = res.data.map(function(element) {
          return {
            created_at: element.created_at,
            lat: element.lat,
            lon: element.lon,
            comment: element.comment
          };
        });
      });
    }
  }
};
</script>

<style>
</style>
