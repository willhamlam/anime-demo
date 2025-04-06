<script setup>
import { motion } from "motion-v";
import { ref } from "vue";

const showSecond = ref(false);
</script>

<template>
  <div class="wrapper">
    <motion.button layout class="button" @click="showSecond = !showSecond">
      Animate
    </motion.button>
    <motion.div layout-id="element" class="second-element" v-if="showSecond" />
    <motion.div layout-id="element" class="element" v-else />
  </div>
</template>

<style>
.wrapper {
  display: grid;
  height: 400px;
  width: 100vw;
  place-items: center;
  background: #0d0d0d;
}

.element {
  width: 48px;
  height: 48px;
  background: #fad658;
  border-radius: 12px;
}

.second-element {
  height: 96px;
  width: 96px;
  background: #fad658;
  border-radius: 12px;
}

.button {
  display: block;
  background: white;
  padding: 8px 16px;
  border-radius: 8px;
  font-size: 14px;
}
</style>
