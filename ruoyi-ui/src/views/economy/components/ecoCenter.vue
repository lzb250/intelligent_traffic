<template>
  <div class="content">
    <div>
      <dv-border-box-8 :reverse="true">
        <div class="head">
          <div class="head_content">
            <h1>2.3</h1>
            <h2>拥堵指数</h2>
          </div>
          <div class="head_content">
            <h1>21.2</h1>
            <h2>平均速度Km/h</h2>
          </div>
        </div>
      </dv-border-box-8>
    </div>

    <div class="body">
      <!-- 温度监测表 -->
      <dv-border-box-6 style="padding:10px">
        <div class="map-content">
          <!-- <baidu-map
            class="map"
            :center="center"
            :zoom="zoom"
            @ready="handler"
            :mapStyle="mapStyle"
            :scroll-wheel-zoom="true"
          /> -->
          <img :src="crossroad" class="cross">
        </div>
      </dv-border-box-6>
    </div>
  </div>
</template>

<script>
// import Echart from "@/common/echart/index.vue";
import mapStyle from "@/assets/mapStyle.json";
import crossroad from '@/assets/traffic_images/red2green.gif'

export default {
  components: {},
  data() {
    return {
      center: { lng: 0, lat: 0 },
      zoom: 3,
      mapStyle: {
        styleJson: mapStyle,
      },
      crossroad: crossroad + '?' + +new Date()
    };
    
  },
  methods: {
    handler({ BMap, map }) {
      console.log(BMap, map);
      this.center.lng = 106.505;
      this.center.lat = 29.5332;
      this.zoom = 15;
    },
  },
};
</script>

<style scoped>
.content {
  width: 38%;
}
.head {
  padding: 10px;
  height: 80px;
  display: flex;
  justify-content: space-around;
}
.head_content {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
}
.body {
  margin-top: 10px;
}
.body_table1 {
  display: flex;
}
.map-content {
  width: 700px;
  height: 750px;
  overflow: hidden;
}
.map {
  width: 100%;
  height: 100%;
}

.cross {
  width: auto;
  height: auto;
}
</style>
