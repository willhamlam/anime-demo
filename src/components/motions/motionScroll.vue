<template>
  <article id="gallery">
    <header>
      <h2>Lines of London</h2>
    </header>
    <section class="img-group-container" ref="containerRef">
      <div>
        <motion.ul
          class="img-group"
          :style="{ translateX: `-${scrollYProgressValue * 400}vw` }"
        >
          <li class="img-container">
            <img src="@/assets/photos/1.jpg" />
            <h3>#001</h3>
          </li>
          <li class="img-container">
            <img src="@/assets/photos/1.jpg" />
            <h3>#002</h3>
          </li>
          <li class="img-container">
            <img src="@/assets/photos/1.jpg" />
            <h3>#003</h3>
          </li>
          <li class="img-container">
            <img src="@/assets/photos/1.jpg" />
            <h3>#004</h3>
          </li>
          <li class="img-container">
            <img src="@/assets/photos/1.jpg" />
            <h3>#005</h3>
          </li>
        </motion.ul>
      </div>
    </section>
    <footer>
      <p>
        Photos by
        <a target="_blank" href="https://twitter.com/mattgperry">Matt Perry</a>
      </p>
    </footer>
  </article>
  <motion.div
    class="progress"
    :style="{ scaleX: scrollYProgress }"
  ></motion.div>
</template>

<script setup>
import { motion, useScroll, useMotionValueEvent } from "motion-v";
import { ref, onMounted, computed } from "vue";

const containerRef = ref(null);
const scrollYProgressValue = ref(0);
const { scrollYProgress } = useScroll({
  target: containerRef,
});

useMotionValueEvent(scrollYProgress, "change", (latest) => {
  scrollYProgressValue.value = latest;
  console.log(scrollYProgressValue.value);
});

// onMounted(() => {
//   const items = document.querySelectorAll(".img-container");
//   // Animate gallery horizontally during vertical scroll
//   scroll(
//     animate(".img-group", {
//       transform: ["none", `translateX(-${items.length - 1}00vw)`],
//     }),
//     { target: document.querySelector(".img-group-container") }
//   );
//   // Progress bar representing gallery scroll
//   scroll(animate(".progress", { scaleX: [0, 1] }), {
//     target: document.querySelector(".img-group-container"),
//   });
// });
</script>

<style>
#gallery {
  width: 98vw;
}

#gallery h3 {
  font-family: "Azeret Mono", monospace;
}

#gallery header,
#gallery footer {
  height: 70vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.img-group-container {
  height: 500vh;
  position: relative;
}

.img-group-container > div {
  position: sticky;
  top: 0;
  overflow: hidden;
  height: 100vh;
}

.img-group {
  display: flex;
}

.img-container {
  display: flex;
  width: 100vw;
  height: 100vh;
  flex: 0 0 auto;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

#gallery header h2 {
  font-size: 56px;
  font-weight: 700;
  letter-spacing: -3px;
  line-height: 1.2;
  text-align: center;
  margin: 0;
}

.img-container h3 {
  margin: 0;
  font-size: 50px;
  font-weight: 700;
  letter-spacing: -3px;
  line-height: 1.2;
  position: relative;
  bottom: 30px;
  display: inline-block;
}

.img-container img {
  width: 300px;
  height: 400px;
}

.progress {
  position: fixed;
  left: 0;
  right: 0;
  height: 5px;
  background: #9911ff;
  bottom: 50px;
  transform: scaleX(0);
}
</style>
