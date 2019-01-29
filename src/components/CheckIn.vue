<template>
  <div class="containers">
    <div class="nes-container is-dark with-title">
      <p class="title">Check In</p>
      <div style="text-align: left;">
        <i class="nes-icon trophy is-small"></i>
        <label>Lat</label>
        <input type="text" v-model="lat" class="input-text">
        <i class="nes-icon trophy is-small"></i>
        <label>Lon</label>
        <input type="text" v-model="lon" class="input-text">
      </div>
      <div style="text-align: left;">
        <label>Comment</label>
      </div>
      <div style="text-align: left;">
        <input type="text" v-model="comment">
      </div>
      <div style="text-align: right;">
        <button @click="checkIn" class="checkin nes-btn">CheckIn</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CheckIn",
  data: function() {
    return {
      lat: "",
      lon: "",
      comment: ""
    };
  },
  methods: {
    checkIn: function(e) {
      if (!navigator.geolocation) {
        alert("disable geolocation.");
        return;
      }
      navigator.geolocation.getCurrentPosition(
        position => {
          console.log(
            "get:" + position.coords.latitude + "," + position.coords.longitude
          );
          this.lat = position.coords.latitude;
          this.lon = position.coords.longitude;

          var qs = require("qs");
          axios
            .post(
              "http://localhost:3000/place_records.json",
              qs.stringify({
                place_record: {
                  lat: this.lat,
                  lon: this.lon,
                  comment: this.comment
                }
              }),
              {
                headers: { "Content-Type": "application/x-www-form-urlencoded" }
              }
            )
            .then(res => {
              // ここでリスト更新したい
            });
        },
        error => {
          switch (error.code) {
            case 1:
              alert("Permission denided");
              break;
            case 2:
              alert("Position unavailable");
              break;
            case 3:
              alert("Timeout");
              break;
            default:
              alert("error:(" + error.code + ")");
              break;
          }
        }
      );
    }
  }
};
</script>

<style>
.containers {
  margin: 5px;
}
.input-text {
  width: 120px;
}
</style>
