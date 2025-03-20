<template>
  <div class="svg-container">
    <object ref="svgObject" type="image/svg+xml" data="@/assets/RoxyBrowser.svg" class="svg-content"></object>
  </div>
</template>

<script>
import anime from 'animejs';

export default {
  name: 'FontAnime',
  mounted() {
    // 等待SVG加载完成
    this.$refs.svgObject.addEventListener('load', () => {
      const svgDoc = this.$refs.svgObject.contentDocument;
      const paths = svgDoc.querySelectorAll('path');
      
      // 设置所有路径的初始状态
      paths.forEach(path => {
        // 获取路径长度
        const pathLength = path.getTotalLength();
        
        // 设置初始样式
        path.style.strokeDasharray = pathLength;
        path.style.strokeDashoffset = pathLength;
        path.style.fillOpacity = 0;
        
        path.style.stroke = path.getAttribute('fill') || '#000';
        path.style.strokeWidth = '1';
        path.style.fill = 'none'; // 动画开始时不显示填充
      });
      
      // 创建动画
      anime({
        targets: Array.from(paths),
        strokeDashoffset: [anime.setDashoffset, 0],
        fillOpacity: [0, 1],
        easing: 'easeInOutSine',
        duration: 2000,
        delay: (el, i) => i * 250,
        direction: 'normal',
      });
    });
  }
}
</script>

<style scoped>
.svg-container {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.svg-content {
  max-width: 100%;
  height: auto;
}
</style>