<template>
  <button 
    ref="buttonRef"
    :class="[
      'relative rounded-lg px-6 py-2 font-medium backdrop-blur-xl transition-shadow duration-300 ease-in-out hover:shadow dark:bg-[radial-gradient(circle_at_50%_0%,hsl(var(--primary)/10%)_0%,transparent_60%)] dark:hover:shadow-[0_0_20px_hsl(var(--primary)/10%)]',
      props.class
    ]"
  >
    <Motion
      as="span"
      class="relative block size-full text-sm uppercase tracking-wide text-[rgb(0,0,0,65%)] dark:font-light dark:text-[rgb(255,255,255,90%)]"
      :style="{ 
        maskImage: 'linear-gradient(-75deg,hsl(var(--primary)) calc(var(--x) + 20%),transparent calc(var(--x) + 30%),hsl(var(--primary)) calc(var(--x) + 100%))'
      }"
      :animate="{ '--x': '-100%' }"
      :initial="{ '--x': '100%' }"
      :transition="{
        repeat: Infinity,
        repeatType: 'loop',
        repeatDelay: 1,
        type: 'spring',
        stiffness: 20,
        damping: 15,
        mass: 2
      }"
    >
      <slot></slot>
    </Motion>
    <Motion 
      as="span"
      class="absolute inset-0 z-10 block rounded-[inherit] bg-[linear-gradient(-75deg,hsl(var(--primary)/10%)_calc(var(--x)+20%),hsl(var(--primary)/50%)_calc(var(--x)+25%),hsl(var(--primary)/10%)_calc(var(--x)+100%))] p-px"
      :style="{
        mask: 'linear-gradient(rgb(0,0,0), rgb(0,0,0)) content-box,linear-gradient(rgb(0,0,0), rgb(0,0,0))',
        maskComposite: 'exclude'
      }"
      :animate="{ '--x': '-100%' }"
      :initial="{ '--x': '100%' }"
      :transition="{
        repeat: Infinity,
        repeatType: 'loop',
        repeatDelay: 1,
        type: 'spring',
        stiffness: 20,
        damping: 15,
        mass: 2
      }"
    ></Motion>
  </button>
</template>

<script setup lang="ts">
import { Motion } from "motion-v";
import { ref } from "vue";

interface Props {
  class?: string;
}

const props = withDefaults(defineProps<Props>(), {
  class: ''
});

const buttonRef = ref(null);
</script>

<style scoped>
button {
  --x: 100%;
}
</style> 