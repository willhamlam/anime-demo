<template>
  <div class="overlay-container">
    <div class="app-wrapper">
      <AnimatePresence>
        <motion.div
          class="overlay"
          v-if="isLocked"
          :initial="{ opacity: 0, scale: 0.98, backdropFilter: 'blur(0px)' }"
          :animate="{ opacity: 1, scale: 1, backdropFilter: 'blur(20px)' }"
          :exit="{ opacity: 0, scale: 0.98, backdropFilter: 'blur(0px)' }"
          :transition="{ duration: 0.25, ease: 'easeInOut' }"
        >
          <motion.div
            :initial="{ y: isLocked ? -50 : 0 }"
            :animate="{ y: isLocked ? 0 : -50 }"
            :transition="{ duration: 0.8, ease: [0, 0.71, 0.2, 1.01] }"
          >
            <img src="@/assets/lock.png" alt="" class="lock-img" />
          </motion.div>
          <div class="globe-atmosphere"></div>
          <Particles
            :density="300"
            color="#ffffff"
            :size="1.8"
            :speed="0.2"
            class="globe-particles"
            :minOpacity="0.6"
          />
          <motion.div
            :initial="{ scale: isLocked ? 0.9 : 1 }"
            :animate="{ scale: isLocked ? 1 : 0.8 }"
            :transition="{ duration: 0.8, ease: [0, 0.71, 0.2, 1.01] }"
            class="globe-outline"
          ></motion.div>
          <motion.div
            :initial="{ scale: isLocked ? 0.9 : 1 }"
            :animate="{ scale: isLocked ? 1 : 0.8 }"
            :transition="{ duration: 0.8, ease: [0, 0.71, 0.2, 1.01] }"
            class="globe"
          ></motion.div>
        </motion.div>
      </AnimatePresence>
      <motion.div
        :animate="{ scale: isLocked ? 0.98 : 1 }"
        :transition="{ duration: 0.25, ease: 'easeInOut' }"
      >
        <img src="@/assets/dashboard.png" class="app-img" />
      </motion.div>
    </div>
    <button @click="isLocked = !isLocked">Toggle Lock</button>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { motion, AnimatePresence } from "motion-v";
import Particles from "./Particles.vue";

const isLocked = ref(true);
</script>

<style lang="scss" scoped>
.app-wrapper {
  position: relative;
  background-color: #f5fbff;
  width: 1080px;
  height: auto;
  overflow: hidden;
  .globe-particles {
    position: absolute;
    width: 100%;
    height: 400px;
    bottom: -20%;
    z-index: 999;
    mix-blend-mode: hard-light;
    -webkit-mask-image: radial-gradient(50% 60%, #000000, transparent 70%);
    mask-image: radial-gradient(50% 60%, #000000, transparent 70%);
  }
  .globe-atmosphere {
    position: absolute;
    width: 140%;
    height: 400px;
    bottom: -30%;
    background-image: radial-gradient(
      circle at 50% 185%,
      #1697ff,
      rgba(255, 255, 255, 0) 70%
    );
  }
  .globe-outline {
    position: absolute;
    width: 100%;
    height: 100%;
    bottom: calc(-92% + 1px);
    background-color: #ffffff;
    border-radius: 100%;
    opacity: 1;
    z-index: 998;
    box-shadow: rgb(204 211 255) 0px -10px 50px 1px;
  }
  .globe {
    position: absolute;
    width: 100%;
    height: 100%;
    bottom: -92%;
    /* background-color: hsl(204 90% 87% / 1); */
    background-image: radial-gradient(
      circle at 50% 50%,
      #1697ff,
      rgba(255, 255, 255, 0) 70%
    );
    border-radius: 100%;
    box-shadow: rgba(0, 0, 0, 0) 0px 0px 0px 0px,
      rgba(0, 0, 0, 0) 0px 0px 0px 0px,
      rgb(255, 255, 255) 0px 6px 20px 0px inset;
    z-index: 1000;
  }
  .app-img {
    width: 100%;
  }
  .overlay {
    background-color: rgba(255, 255, 255, 0.5);
    // backdrop-filter: blur(30px);
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 2;
  }
  .lock-img {
    width: 240px;
  }
}

.overlay-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  button {
    margin-top: 20px;
  }
}
</style>
