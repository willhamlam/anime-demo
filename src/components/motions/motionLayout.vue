<script setup>
import { motion } from "motion-v";
import { ref } from "vue";

const isOpen = ref(false);
const layout = ref(false);
</script>

<template>
  <div class="motion-layout-wrapper">
    <motion.div
      layout
      class="element"
      :class="isOpen ? 'open' : ''"
      @click="isOpen = !isOpen"
      :transition="{ type: 'spring', duration: 0.5 }"
    ></motion.div>
    <div style="height: 100px"></div>
    <button @click="layout = !layout">Change layout</button>
    <motion.ul layout class="layout-tabs" :class="layout ? 'row' : ''">
      <motion.li layout-id="profiles">Profiles</motion.li>
      <motion.li layout-id="projects">Projects</motion.li>
      <motion.li layout-id="extensions">Extensions</motion.li>
      <motion.li layout-id="proxies">Proxies</motion.li>
    </motion.ul>
  </div>
</template>

<style lang="scss" scoped>
.motion-layout-wrapper {
  position: relative;
}
.layout-tabs {
  display: flex;
  flex-direction: column;
  gap: 8px;
  &.row {
    display: flex;
    flex-direction: row;
  }
  li {
    width: 100px;
    padding: 4px 8px;
    border-radius: 8px;
    color: rgb(205, 205, 205);
    cursor: pointer;
  }
}
.element {
  width: 48px;
  height: 48px;
  background: #fad658;
  cursor: pointer;
  border-radius: 8px;
  &.open {
    position: absolute;
    top: -200px;
    left: -48px;
    width: 100px;
    height: 100px;
    border-radius: 16px;
  }
}
</style>
