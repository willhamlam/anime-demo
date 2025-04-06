<script setup>
import { ref, reactive, useTemplateRef } from "vue";
import { useElementSize } from "@vueuse/core";
import { motion } from "motion-v";
const showExtraContent = ref(false);

const toggleHeight = () => {
  showExtraContent.value = !showExtraContent.value;
};

const el = useTemplateRef("el");
const size = reactive(
  useElementSize(el, { width: 0, height: 0 }, { box: "border-box" })
);
</script>

<template>
  <div class="motion-height-wrapper">
    <button class="button" @click="toggleHeight">Toggle height</button>
    <p style="color: white">{{ size.height }}</p>
    <motion.div
      :animate="{ height: size.height, transition: 0.1 }"
      class="element"
    >
      <div class="inner" ref="el">
        <h1>Fake Family Drawer</h1>
        <p>
          This is a fake family drawer. Animating height is tricky, but
          satisfying when it works.
        </p>
        <p v-show="showExtraContent">
          This extra content will change the height of the drawer. Some even
          more content to make the drawer taller and taller and taller...
        </p>
      </div>
    </motion.div>
  </div>
</template>

<style lang="scss" scoped>
.motion-height-wrapper {
  display: grid;
  height: 100vh;
  width: 100vw;
  place-items: center;
  background: #0d0d0d;
  color: #000;
}

.element {
  background: white;
  border-radius: 16px;
  width: 320px;
  display: flex;
  flex-direction: column;
  gap: 8px;
  overflow: hidden;
}

.inner {
  padding: 13px 16px;
}

.element h1 {
  font-weight: 600;
}

.element p {
  color: #63635d;
}

.button {
  background: white;
  padding: 8px 16px;
  border-radius: 8px;
  font-size: 14px;
}
</style>
