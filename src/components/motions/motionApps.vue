<template>
  <div>
    <AnimatePresence>
      <motion.div
        :initial="{ opacity: 0 }"
        :animate="{ opacity: 0.5 }"
        :exit="{ opacity: 0 }"
        v-if="activeGame"
        class="overlay"
      ></motion.div>
    </AnimatePresence>

    <div v-if="activeGame" class="active-game">
      <motion.div
        :layout-id="`game-${activeGame.title}`"
        class="inner"
        ref="gameRef"
        :style="{ borderRadius: '12px' }"
      >
        <div class="header">
          <motion.img
            :layout-id="`image-${activeGame.title}`"
            height="56"
            width="56"
            alt=""
            :src="activeGame.image"
            :style="{ borderRadius: '12px' }"
          />
          <div class="header-inner">
            <div class="content-wrapper">
              <motion.h2
                :layout-id="`title-${activeGame.title}`"
                class="game-title"
                >{{ activeGame.title }}</motion.h2
              >
              <motion.p
                :layout-id="`description-${activeGame.title}`"
                class="game-description"
                >{{ activeGame.description }}</motion.p
              >
            </div>
            <motion.button
              :layout-id="`button-${activeGame.title}`"
              class="button"
            >
              Get
            </motion.button>
          </div>
        </div>
        <AnimatePresence>
          <motion.p
            :key="`long-description-${activeGame.title}`"
            :initial="{ opacity: 0 }"
            :animate="{ opacity: 1 }"
            :exit="{ opacity: 1, transition: { duration: 0.8 } }"
            class="long-description"
          >
            {{ activeGame.longDescription }}
          </motion.p>
        </AnimatePresence>
      </motion.div>
    </div>

    <ul class="list">
      <motion.li
        :layout-id="`game-${game.title}`"
        v-for="game in games"
        :key="game.title"
        @click="setActiveGame(game)"
        :style="{ borderRadius: '8px' }"
        class="game-item"
      >
        <motion.img
          :layout-id="`image-${game.title}`"
          height="56"
          width="56"
          alt=""
          :src="game.image"
          :style="{ borderRadius: '12px' }"
        />
        <div class="game-wrapper">
          <div class="content-wrapper">
            <motion.h2 :layout-id="`title-${game.title}`" class="game-title">{{
              game.title
            }}</motion.h2>
            <motion.p
              :layout-id="`description-${game.title}`"
              class="game-description"
              >{{ game.description }}</motion.p
            >
          </div>
          <motion.button :layout-id="`button-${game.title}`" class="button">
            Get
          </motion.button>
        </div>
      </motion.li>
    </ul>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import { onClickOutside } from "@vueuse/core";
import { motion, AnimatePresence } from "motion-v";
const activeGame = ref(null);
const gameRef = ref(null);

const setActiveGame = (game) => {
  activeGame.value = game;
};

onClickOutside(gameRef, () => {
  activeGame.value = null;
});

onMounted(() => {
  const onKeyDown = (event) => {
    if (event.key === "Escape") {
      activeGame.value = null;
    }
  };

  window.addEventListener("keydown", onKeyDown);

  onUnmounted(() => {
    window.removeEventListener("keydown", onKeyDown);
  });
});

const games = [
  {
    title: "The Oddysey",
    description: "Explore unknown galaxies.",
    longDescription:
      "Throughout their journey, players will encounter diverse alien races, each with their own unique cultures and technologies. Engage in thrilling space combat, negotiate complex diplomatic relations, and make critical decisions that affect the balance of power in the galaxy.",
    image:
      "https://animations-on-the-web-git-how-i-use-3066e1-emilkowalski-s-team.vercel.app/how-i-use-framer-motion/how-i-code-animations/space.png",
  },
  {
    title: "Angry Rabbits",
    description: "They are coming for you.",
    longDescription:
      "The rabbits are angry and they are coming for you. You have to defend yourself with your carrot gun. The game is not simple, you have to be fast and accurate to survive.",
    image:
      "https://animations-on-the-web-git-how-i-use-3066e1-emilkowalski-s-team.vercel.app/how-i-use-framer-motion/how-i-code-animations/rabbit.png",
  },
  {
    title: "Ghost town",
    description: "Find the ghosts.",
    longDescription:
      "You are in a ghost town and you have to find the ghosts. But be careful, they are dangerous.",
    image:
      "https://animations-on-the-web-git-how-i-use-3066e1-emilkowalski-s-team.vercel.app/how-i-use-framer-motion/how-i-code-animations/ghost.webp",
  },
  {
    title: "Pirates in the jungle",
    description: "Find the treasure.",
    longDescription:
      "You are a pirate and you have to find the treasure in the jungle. But be careful, there are traps and wild animals.",
    image:
      "https://animations-on-the-web-git-how-i-use-3066e1-emilkowalski-s-team.vercel.app/how-i-use-framer-motion/how-i-code-animations/pirate.png",
  },
  {
    title: "Lost in the mountains",
    description: "Find your way home.",
    longDescription:
      "You are lost in the mountains and you have to find your way home. But be careful, there are dangerous animals and you can get lost.",
    image:
      "https://animations-on-the-web-git-how-i-use-3066e1-emilkowalski-s-team.vercel.app/how-i-use-framer-motion/how-i-code-animations/boy.webp",
  },
];
</script>

<style scoped>
.overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 1);
  z-index: 10;
}

.active-game {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 20;
  width: 90%;
  max-width: 500px;
}

.inner {
  background-color: white;
  padding: 20px;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
}

.header {
  display: flex;
  gap: 15px;
  margin-bottom: 20px;
}

.header-inner {
  display: flex;
  flex-grow: 1;
  justify-content: space-between;
  align-items: center;
}

.list {
  list-style: none;
  padding: 0;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.list li {
  display: flex;
  padding: 10px;
  cursor: pointer;
  gap: 15px;
  background-color: #f8f8f8;
}

.game-wrapper {
  display: flex;
  flex-grow: 1;
  justify-content: space-between;
  align-items: center;
}

.button {
  padding: 8px 16px;
  background-color: #0066ff;
  color: white;
  border: none;
  border-radius: 20px;
  cursor: pointer;
}

.game-title {
  margin: 0;
  font-size: 16px;
}

.game-description {
  margin: 0;
  color: #666;
  font-size: 14px;
}

.long-description {
  line-height: 1.5;
  color: #333;
}
</style>
