<script setup>
import { ref } from "vue";
import { motion, AnimatePresence } from "motion-v";
import IconCopy from "@/components/icons/IconCopy.vue";
import IconCheck from "@/components/icons/IconCheck.vue";

const isCopied = ref(false);
const sendLinkStatus = ref("ready");
const toggleCopied = () => {
  isCopied.value = !isCopied.value;
  setTimeout(() => {
    isCopied.value = false;
  }, 2000);
};

const sendLink = () => {
  sendLinkStatus.value = "sending";

  setTimeout(() => {
    sendLinkStatus.value = "sent";
  }, 2000);

  setTimeout(() => {
    sendLinkStatus.value = "ready";
  }, 4000);
};

const variants = {
  hidden: { y: -25 },
  visible: { y: 0 },
  exit: { y: 25, opacity: 0 },
  transition: { type: "spring", bounce: 0, duration: 0.3 },
};
</script>

<template>
  <div class="button-container">
    <button class="button" @click="toggleCopied" :disabled="isCopied">
      <AnimatePresence mode="wait" :initial="false">
        <motion.span
          v-if="!isCopied"
          :initial="{ opacity: 0, scale: 0.8 }"
          :animate="{ opacity: 1, scale: 1 }"
          :exit="{ opacity: 0, scale: 0.8 }"
          :transition="{
            duration: 0.1,
          }"
        >
          <IconCopy />
          Copy
        </motion.span>
        <motion.span
          v-if="isCopied"
          :initial="{ opacity: 0, scale: 0.8 }"
          :animate="{ opacity: 1, scale: 1 }"
          :exit="{ opacity: 0, scale: 0.8 }"
          :transition="{
            duration: 0.1,
          }"
        >
          <IconCheck />
          Copied!
        </motion.span>
      </AnimatePresence>
    </button>
    <button class="button" @click="sendLink">
      <AnimatePresence mode="wait" :initial="false">
        <motion.span
          v-if="sendLinkStatus === 'ready'"
          :variants="variants"
          initial="hidden"
          animate="visible"
          exit="exit"
          transition="transition"
          >Send me a link</motion.span
        >
        <motion.span
          v-if="sendLinkStatus === 'sending'"
          :initial="{ y: -25 }"
          :animate="{ y: 0 }"
          :exit="{ y: 25, opacity: 0 }"
          :transition="{ type: 'spring', bounce: 0, duration: 0.3 }"
          >Sending...</motion.span
        >
        <motion.span
          v-if="sendLinkStatus === 'sent'"
          :initial="{ y: -25 }"
          :animate="{ y: 0 }"
          :exit="{ y: 25, opacity: 0 }"
          :transition="{ type: 'spring', bounce: 0, duration: 0.3 }"
          >Sent!</motion.span
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
