<script setup>
import { motion } from "motion-v"
</script>

<template>
    <motion.div
        class="ball"
        :initial="{ opacity: 0, scale: 0.5 }"
        :animate="{ opacity: 1, scale: 1 }"
        :transition="{
            duration: 0.8,
            delay: 0.5,
            ease: [0, 0.71, 0.2, 1.01]
        }"
    />
</template>

<style>
.ball {
    width: 200px;
    height: 200px;
    border-radius: 50%;
    background: blue;
}
</style>