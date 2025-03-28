<script setup>
import GithubGlobe from '@/components/GithubGlobe.vue';
// import ShinyButton from '@/components/ShinyButton.vue';

const globeConfig = {
  globeColor: '#fff', // 灰色
  polygonColor: '#000', // 黑色
};
</script>

<template>
  <div class="flex h-screen items-center justify-center">
    <GithubGlobe :globe-config="globeConfig" class="w-[1000px] h-[1000px]" />
  </div>
</template>