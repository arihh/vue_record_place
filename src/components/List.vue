<template>
  <div class="containers">
    <table class="table nes-table is-bordered is-dark">
      <thead>
        <tr>
          <th>Time</th>
          <th>Lat</th>
          <th>Lon</th>
          <th>Comment</th>
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
import moment from "moment";

export default {
  name: "List",
  props: ["items"],
  methods: {
    loadPlaces: function(e, index) {
      axios.get("http://localhost:3000/place_records.json").then(res => {
        console.log(res.data);
        moment.lang("ja");
        this.items = res.data.map(function(element) {
          return {
            created_at: moment(element.created_at).format(
              "YYYY/MM/DD HH:mm:ss"
            ),
            lat: element.lat,
            lon: element.lon,
            comment: element.comment
          };
        });
      });
    }
  },
  mounted() {
    this.loadPlaces();
  }
};
</script>

<style>
.containers {
  margin: 5px;
}
.table {
  width: 100%;
}
</style>
