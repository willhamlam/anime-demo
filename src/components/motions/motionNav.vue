<script setup>
import { ref } from "vue";
import { motion, AnimatePresence } from "motion-v";

const showSubNav = ref(false);
const subNavs = ref(["Project", "Project", "Project"]);
const addProject = () => {
  subNavs.value.push("Project");
};
</script>

<template>
  <div>
    <button @click="addProject">Add project</button>
    <ul layout class="nav">
      <li class="nav-item"><div class="content">Profiles</div></li>
      <li class="nav-item">
        <div class="content" @click="showSubNav = !showSubNav">Projects</div>
        <AnimatePresence :initial="false">
          <motion.ul
            layout
            :initial="{ height: '0px', opacity: 0, y: -40 }"
            :animate="{ height: 'auto', opacity: 1, y: 0 }"
            :exit="{ height: '0px', opacity: 0, y: -40 }"
            :transition="{
              duration: 0.6,
              ease: [0, 0.71, 0.2, 1.01],
              opacity: { duration: 0.3, ease: 'backOut' },
            }"
            class="sub-nav"
            v-if="showSubNav"
          >
            <li layout v-for="nav in subNavs" :key="nav" class="sub-nav-item">
              {{ nav }}
            </li>
          </motion.ul>
        </AnimatePresence>
      </li>
      <li class="nav-item">
        <div class="content">Proxies</div>
      </li>
      <li class="nav-item">
        <div class="content">Accounts</div>
      </li>
      <li class="nav-item">
        <div class="content">Extensions</div>
      </li>
    </ul>
  </div>
</template>

<style lang="scss" scoped>
.nav {
  margin-top: 200px;
  .content {
    position: relative;
    z-index: 2;
    min-width: 160px;
    padding: 8px 16px;
    color: #adadad;
    cursor: pointer;
    transition: all 0.15s ease;
    border-radius: 4px;
    background-color: #0d0d0d;
    &:hover {
      background-color: #1d1d1d;
      color: #ffffff;
    }
  }
  .sub-nav {
    position: relative;
    z-index: 1;
    margin-left: 24px;
    border-left: 1px solid #303030;
    .sub-nav-item {
      color: #adadad;
      padding: 8px 16px;
      margin: 0 4px;
      border-radius: 4px;
      cursor: pointer;
      transition: all 0.15s ease;
      &:hover {
        background-color: #1d1d1d;
        color: #ffffff;
      }
    }
  }
}
</style>
