<script setup>
import { motion } from "motion-v";
</script>

<template>
  <div class="container">
    <motion.div
      class="ball"
      :initial="{ opacity: 0, scale: 0.5 }"
      :animate="{ opacity: 1, scale: 1 }"
      :transition="{
        type: 'spring',
        bounce: 0.6,
      }"
    />
  </div>
</template>

<style>
.container {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
.ball {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  background: #fad658;
}
</style>
