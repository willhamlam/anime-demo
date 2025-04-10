<template>
    <div class="overlay-container">
        <div class="app-wrapper">
            <AnimatePresence>
                <motion.div class="overlay" v-if="isLocked" 
                    :initial="{ opacity: 0, scale: 0.98, backdropFilter: 'blur(0px)' }" 
                    :animate="{ opacity: 1, scale: 1, backdropFilter: 'blur(20px)' }"
                    :exit="{ opacity: 0, scale: 0.98, backdropFilter: 'blur(0px)' }"
                    :transition="{ duration: 0.25, ease: 'easeInOut' }"
                >
                    <img src="@/assets/lock.png" alt="" class="lock-img">
                </motion.div>
            </AnimatePresence>
            <motion.div 
                :animate="{ scale: isLocked ? 0.98 : 1 }" 
                :transition="{ duration: 0.25, ease: 'easeInOut' }"
            >
                <img src="@/assets/dashboard.png" class="app-img" >
            </motion.div> 
        </div>
        <button @click="isLocked = !isLocked">Toggle Lock</button>
    </div>
</template>

<script setup>
import { ref } from 'vue';
import { motion, AnimatePresence } from 'motion-v';

const isLocked = ref(false);
</script>

<style lang="scss" scoped>
.app-wrapper {
    position: relative;
    background-color: #F5FBFF;
    width: 1080px;
    height: auto;
    .app-img {
        width: 100%;
    }
    .overlay {
        background-color: rgba(255, 255, 255, 0.5);
        // backdrop-filter: blur(30px);
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        z-index: 2;
    }
    .lock-img {
        margin-top: 200px;
        width: 240px;
    }
}

.overlay-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    button {
        margin-top: 20px;
    }
}
</style>


