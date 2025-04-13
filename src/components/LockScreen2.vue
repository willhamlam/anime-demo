<template>
  <div class="lock-container">
    <div class="lock-screen">
      <img src="@/assets/lockscreen/monintor5.svg" class="monitor" />
      <img src="@/assets/lockscreen/lock.svg" class="lock" />
      <Particles :density="50" :speed="0.4" class="particles particles-mask" />
      <div class="light-box">
        <motion.div
          :initial="{ opacity: 0, rotate: '-30deg' }"
          :animate="{ opacity: 0.32, rotate: '-30deg' }"
          class="beam beam1"
        ></motion.div>
        <motion.div
          :initial="{ opacity: 0, rotate: '-20deg' }"
          :animate="{ opacity: 0.24, rotate: '-20deg' }"
          class="beam beam2"
        ></motion.div>
        <motion.div
          :initial="{ opacity: 0, rotate: '15deg' }"
          :animate="{ opacity: 0.4, rotate: '15deg' }"
          class="beam beam3"
        ></motion.div>
        <motion.div
          :initial="{ opacity: 0, rotate: '30deg' }"
          :animate="{ opacity: 0.36, rotate: '30deg' }"
          class="beam beam4"
        ></motion.div>
        <motion.div
          :initial="{ opacity: 0, rotate: '0deg' }"
          :animate="{ opacity: 0.24, rotate: '0deg' }"
          class="beam beam5"
        ></motion.div>
      </div>
    </div>
    <p>RoxyBrowser has been locked</p>
  </div>
</template>

<script setup>
import { motion } from "motion-v";
import Particles from "./motions/Particles.vue";
</script>

<style lang="scss" scoped>
p {
  text-align: center;
  color: white;
  opacity: 0.5;
  margin-top: 40px;
}
.lock-screen {
  position: relative;
  .monitor {
    position: absolute;
    top: 130px;
    left: 50%;
    transform: translateX(-50%);
  }
  .lock {
    position: absolute;
    top: 30px;
    left: 50%;
    transform: translateX(-50%);
    scale: 0.8;
    opacity: 0.6;
    transform-origin: left;
  }
}
.particles {
  position: absolute;
  top: 0px;
  left: 0px;
  width: 300px;
  height: 150px;
}
.particles-mask {
  mask-image: radial-gradient(50% 50%, white, transparent 85%);
  -webkit-mask-image: radial-gradient(50% 50%, white, transparent 85%);
}
.light-box {
  position: relative;
  width: 300px;
  height: 200px;
  clip-path: rect(0px 300px 155px 0px);
  /* clip-path: path(
    "M-25 -5H327L232.889 143.696C229.222 149.489 222.845 153 215.989 153H86.011C79.155 153 72.7777 149.489 69.1114 143.696L-25 -5Z"
  ); */
  .beam {
    background: linear-gradient(
      0deg,
      rgba(255, 255, 255, 0) 0%,
      rgba(255, 255, 255, 1) 6%,
      rgba(255, 255, 255, 0) 90%
    );
    mask: linear-gradient(
      90deg,
      rgba(0, 0, 0, 0) 0%,
      rgba(0, 0, 0, 0.5) 35%,
      rgba(0, 0, 0, 0.5) 64%,
      rgba(0, 0, 0, 0) 90%
    );
    height: 20vh;
    position: absolute;
    left: 50%;
    margin-top: 5px;
    transform-origin: bottom;
    mix-blend-mode: difference;
    &.beam1 {
      width: 50px;
      margin-left: -70px;
      opacity: 0.32;
    }
    &.beam2 {
      width: 80px;
      margin-left: -65px;
      opacity: 0.4;
    }
    &.beam3 {
      width: 80px;
      margin-left: -20px;
      opacity: 0.4;
    }
    &.beam4 {
      width: 60px;
      margin-left: 15px;
      opacity: 0.36;
    }
    &.beam5 {
      width: 90px;
      margin-left: -45px;
      opacity: 0.45;
    }
  }
}
</style>
