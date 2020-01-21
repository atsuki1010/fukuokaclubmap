<template>
  <div id="app">
  </div>
</template>

<script>
import 'leaflet/dist/leaflet.css';
import L from 'leaflet';

delete L.Icon.Default.prototype._getIconUrl

L.Icon.Default.mergeOptions(
  {
    iconUrl : require('leaflet/dist/images/marker-icon.png'),
    iconRetinaUrl : require('leaflet/dist/images/marker-icon-2x.png'),
    shadowUrl : require('leaflet/dist/images/marker-shadow.png')
  }
);

export default {
    mounted(){
      const map = L.map("app").addLayer(
        L.tileLayer("https://{s}.tile.osm.org/{z}/{x}/{y}.png")
      );

      map.locate({ setView: true, maxZoom: 10});

      function onLocationFound(e){
        var radius = e.accuracy / 2;
        L.marker(e.latlng)
          .addTo(map)
          .bindPopup("あなたの現在地から" + radius + "メートルの場所です")
          .openPopup();

        L.circle(e.latlng, radius).addTo(map);
      }
      map.on("locationfound", onLocationFound);

      function onLocationError(e){
         alert(e.message);
      }
      map.on("locationerror", onLocationError);

      // eslint-disable-next-line no-unused-vars
      const marker = L.marker([33.5934, 130.3949]).addTo(map);
      marker.bindPopup("<p>CLUB Cat’s(クラブキャッツ)</p><p>営業時間：21:00～27:00(日によって異なるため、要確認)</p><p>福岡県福岡市中央区天神3-7-13 第13ラインビル 5F</p><p><a href='http://club-cats.jp/'>お店情報</a></p>").openPopup();

      // eslint-disable-next-line no-unused-vars
      const marker2 = L.marker([33.5882, 130.3955]).addTo(map);
      marker2.bindPopup("<p>CLUB INFINITY FUKUOKA(クラブ インフィニティ)</p><p>営業時間：22:00～29:00(日によって異なるため、要確認)</p><p>福岡県福岡市中央区大名1-12-52 3F</p><p><a href='https://www.instagram.com/infinity_fukuoka/?utm_source=ig_embed'>お店情報</a></p>").openPopup();

      const marker3 = L.marker([33.5930, 130.3947]).addTo(map);
      marker3.bindPopup("<p>CLUB X fukuoka(クラブエックス)</p><p>営業時間：22:00～5:00</p><p>福岡市中央区舞鶴1-8-38 第19ラインビル6F&5F</p><p><a href='https://www.instagram.com/club_x_fukuoka_5f/?utm_source=ig_embed'>お店情報</a></p>").openPopup();

      // eslint-disable-next-line no-unused-vars
      const marker4 = L.marker([33.5888, 130.3957]).addTo(map);
      marker4.bindPopup("<p>Happy Cock(ハッピーコック)</p><p>営業時間：21:00～5:00(日によって異なるため、要確認)</p><p>福岡県福岡市中央区大名2丁目1−51 マウンテン5・9F</p><p><a href='https://www.instagram.com/happycockfuk/?utm_source=ig_embed'>お店情報</a></p>").openPopup();

      // eslint-disable-next-line no-unused-vars
      const marker5 = L.marker([33.5861, 130.3987]).addTo(map);
      marker5.bindPopup("<p>グランドミラージュevoL(エボル)</p><p>営業時間：19:00～26:00</p><p>福岡県福岡市中央区今泉1-17-16</p><p><a href='https://grand-mirage.com/evol/'>お店情報</a></p>").openPopup();

      // eslint-disable-next-line no-unused-vars
      const marker6 = L.marker([33.5883, 130.3959]).addTo(map);
      marker6.bindPopup("<p>ibiza FUKUOKA(イビザフクオカ)</p><p>営業時間：21：00〜5：00</p><p>福岡市中央区大名1-12-56 THE SHOPS 5F</p><p><a href='https://www.ibiza-fukuoka.jp/'>お店情報</a></p>").openPopup();

      // eslint-disable-next-line no-unused-vars
      const marker7 = L.marker([33.5932, 130.4054]).addTo(map);
      marker7.bindPopup("<p>bijou(美獣)</p><p>営業時間：21:00〜翌朝5:00</p><p>福岡市博多区中洲4丁目7-8 ラ・パピヨンビル5Ｆ</p><p><a href='http://bijou-fukuoka.com/'>お店情報</a></p>").openPopup();
    }
};
</script>

<style>
html, body, #app {
  height: 100%;

}
body{
  margin: 0;
}

</style>
