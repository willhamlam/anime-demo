<script setup>
import { ref } from "vue";
import { motion } from "motion-v";

const tabs = ["Home", "Pricing", "Features", "Download"];
const selectedTab = ref(tabs[0]);
</script>

<template>
  <div class="motion-demo">
    <ul class="tabs">
      <li
        v-for="tab in tabs"
        :key="tab"
        class="tab"
        :class="{ active: selectedTab == tab }"
        @click="selectedTab = tab"
      >
        <motion.span
          :animate="{ color: selectedTab === tab ? '#000' : '#fad658' }"
          :transition="{ duration: 0.3 }"
          >{{ tab }}</motion.span
        >
        <motion.div
          class="active-bg"
          v-if="selectedTab == tab"
          layout-id="bg"
          id="bg"
          :transition="{ duration: 0.3, type: 'spring' }"
        />
      </li>
    </ul>
  </div>
</template>

<style lang="scss" scoped>
.progress {
  height: 10px;
  background: #fad658;
  position: sticky;
  top: 0;
  left: 0;
}

.box {
  width: 48px;
  height: 48px;
  background: #fad658;
  border-radius: 12px;
}

.tabs {
  display: flex;
  gap: 12px;
  .tab {
    cursor: pointer;
    padding: 12px 16px;
    width: 100px;
    border-radius: 12px;
    text-align: center;
    position: relative;
    span {
      color: #fad658;
    }
    &.active {
      span {
        position: relative;
        z-index: 2;
        color: #000;
      }
    }
    .active-bg {
      position: absolute;
      z-index: 1;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: #fad658;
      border-radius: 12px;
    }
  }
}
</style>
