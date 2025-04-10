<script setup>
import MotionDemo from "@/components/MotionDemo.vue";
import MotionNav from "@/components/motions/motionNav.vue";
import MotionButton from "@/components/motions/motionButton.vue";
import MotionHeight from "@/components/motions/motionHeight.vue";
import MotionLayout from "@/components/motions/motionLayout.vue";
import MotionLayout2 from "@/components/motions/motionLayout2.vue";
import MotionApps from "@/components/motions/motionApps.vue";
import MotionScroll from "@/components/motions/motionScroll.vue";
import MotionOverlay from "@/components/motions/overlay.vue";
</script>

<template>
  <div class="container">
    <MotionOverlay />
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
</style>
