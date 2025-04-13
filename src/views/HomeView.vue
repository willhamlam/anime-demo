<script setup>
import MotionDemo from "@/components/MotionDemo.vue";
import MotionNav from "@/components/motions/motionNav.vue";
import MotionButton from "@/components/motions/motionButton.vue";
import MotionHeight from "@/components/motions/motionHeight.vue";
import MotionLayout from "@/components/motions/motionLayout.vue";
import MotionLayout2 from "@/components/motions/motionLayout2.vue";
import MotionApps from "@/components/motions/motionApps.vue";
import MotionScroll from "@/components/motions/motionScroll.vue";
import LockScreen from "@/components/LockScreen.vue";
import LockScreen2 from "@/components/LockScreen2.vue";
</script>

<template>
  <div class="container">
    <LockScreen2 />
  </div>
</template>

<style>
.container {
  width: 100%;
  height: 100%;
  /* background-color: #0d0d0d; */
  background-color: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
