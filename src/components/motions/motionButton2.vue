<script setup>
import { ref } from "vue";
import { motion, AnimatePresence } from "motion-v";

const isCopied = ref(false);
const sendLinkStatus = ref("Send me a link");

const sendLink = () => {
  sendLinkStatus.value = "Sending...";

  setTimeout(() => {
    sendLinkStatus.value = "Sent!";
  }, 2000);

  setTimeout(() => {
    sendLinkStatus.value = "Send me a link";
  }, 4000);
};
</script>

<template>
  <div class="button-container">
    <button class="button" @click="sendLink">
      <AnimatePresence mode="popLayout" :initial="false">
        <motion.span
          :key="sendLinkStatus"
          :initial="{ y: -25, opacity: 0 }"
          :animate="{ y: 0, opacity: 1 }"
          :exit="{ y: 25, opacity: 0 }"
          :transition="{ type: 'spring', bounce: 0, duration: 0.3 }"
          >{{ sendLinkStatus }}</motion.span
        >
      </AnimatePresence>
    </button>
  </div>
</template>

<style lang="scss" scoped>
.button-container {
  display: flex;
  gap: 24px;
}
.button {
  position: relative;
  cursor: pointer;
  background-color: #464646;
  padding: 6px 12px;
  border-radius: 4px;
  color: #ffffff;
  font-size: 12px;
  overflow: hidden;
  span {
    display: flex;
    gap: 4px;
    min-width: 100px;
    justify-content: center;
    align-items: center;
  }
  &:hover {
    background-color: #565656;
  }
  svg {
    width: 16px;
  }
}
</style>
