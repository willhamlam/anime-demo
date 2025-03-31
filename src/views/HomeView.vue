<script setup>
import GithubGlobe from "@/components/GithubGlobe.vue";
// import ShinyButton from '@/components/ShinyButton.vue';

const globeConfig = {
  rings: 3,
  maxRings: 5,
  globeColor: "#fff", // 灰色
  polygonColor: "#000", // 黑色
  showAtmosphere: true,
  atmosphereColor: "#000",
  arcTime: 2000, // 弧线动画时间（毫秒）
  arcLength: 0.5, // 弧线长度比例
  autoRotate: true, // 自动旋转
};

const cityConnections = [
  {
    order: 1,
    startLat: 39.9042, // 北京
    startLng: 116.4074,
    endLat: 35.6762, // 东京
    endLng: 139.6503,
    arcAlt: 0.2, // 弧线高度
    color: "#ff0000", // 红色
  },
  {
    order: 2,
    startLat: 51.5074, // 伦敦
    startLng: -0.1278,
    endLat: 40.7128, // 纽约
    endLng: -74.006,
    arcAlt: 0.2,
    color: "#00ff00", // 绿色
  },
  {
    order: 3,
    startLat: 22.3193, // 上海
    startLng: 114.1694,
    endLat: 1.3521, // 新加坡
    endLng: 103.8198,
    arcAlt: 0.2,
    color: "#0000ff", // 蓝色
  },
  // 可以添加更多城市连接
];
</script>

<template>
  <div class="flex h-screen items-center justify-center">
    <GithubGlobe
      :data="cityConnections"
      :globe-config="globeConfig"
      :city-connections="cityConnections"
      class="w-[1000px] h-[1000px]"
    />
  </div>
</template>
