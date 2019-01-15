<template>
  <div>
    <div>
      <label>緯度</label>
      <input type="text" v-model="lat">
      <label>経度</label>
      <input type="text" v-model="lon">
    </div>
    <div>
      <label>コメント</label>
      <input type="text" v-model="comment">
    </div>
    <button @click="checkIn" class="checkin btn btn-primary">チェックイン!</button>
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
        alert("位置情報が取れません");
        return;
      }
      navigator.geolocation.getCurrentPosition(
        position => {
          console.log(
            "取得:" + position.coords.latitude + "," + position.coords.longitude
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
              //リクエスト成功時の処理
            });
        },
        error => {
          switch (error.code) {
            case 1: //PERMISSION_DENIED
              alert("位置情報の利用が許可されていません");
              break;
            case 2: //POSITION_UNAVAILABLE
              alert("現在位置が取得できませんでした");
              break;
            case 3: //TIMEOUT
              alert("タイムアウトになりました");
              break;
            default:
              alert("その他のエラー(エラーコード:" + error.code + ")");
              break;
          }
        }
      );
    }
  }
};
</script>

<style>
</style>
