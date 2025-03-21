<template>
  <div class="profile-list">
    <div class="profile-wrapper">
      <div class="module-wrapper">
        <div class="module-blocks">
          <div class="module">
            <img src="@/assets/windows.svg" alt="" />
          </div>
          <div class="module">
            <img src="@/assets/rx_flag_us.svg" alt="" />
          </div>
          <div class="module">
            <img src="@/assets/rx_site_amazon.svg" alt="" />
          </div>
          <WavyBackground
            class="waveContainer"
            waveWidth="1.2"
            blur="0"
            speed="fast"
            waveOpacity="1"
            :animate="true"
          ></WavyBackground>
        </div>
      </div>
      <p class="profile-name">Untitle profile</p>
    </div>
    <div class="profile-wrapper">
      <div class="module-wrapper">
        <div class="module-blocks">
          <div class="module">
            <img src="@/assets/windows.svg" alt="" />
          </div>
          <div class="module">
            <img src="@/assets/rx_flag_hk.svg" alt="" />
          </div>
          <div class="module">
            <img src="@/assets/rx_site_amazon.svg" alt="" />
          </div>
          <div class="dashline"></div>
        </div>
      </div>
      <p class="profile-name">Untitle profile</p>
    </div>
    <div class="profile-wrapper">
      <div class="module-wrapper">
        <div class="module-blocks">
          <div class="module">
            <img src="@/assets/windows.svg" alt="" />
          </div>
          <!-- <div class="module">
          <img src="@/assets/rx_flag_hk.svg" alt="">
        </div> -->
          <div class="module">
            <img src="@/assets/rx_site_facebook.svg" alt="" />
          </div>
          <div class="dashline"></div>
          <!-- <WavyBackground class="waveContainer" waveWidth="1.2" blur="0" speed="fast" waveOpacity="1" :animate="true"></WavyBackground> -->
        </div>
      </div>
      <p class="profile-name">Untitle profile</p>
    </div>
    <div class="profile-wrapper">
      <div class="module-wrapper">
        <div class="module-blocks">
          <div class="module">
            <img src="@/assets/windows.svg" alt="" />
          </div>
          <!-- <div class="module">
          <img src="@/assets/rx_flag_hk.svg" alt="">
        </div> -->
          <div class="module">
            <img src="@/assets/rx_site_shopify.svg" alt="" />
          </div>
          <div class="dashline"></div>
          <!-- <WavyBackground class="waveContainer" waveWidth="1.2" blur="0" speed="fast" waveOpacity="1" :animate="true"></WavyBackground> -->
        </div>
      </div>
      <p class="profile-name">Untitle profile</p>
    </div>
    <div class="profile-wrapper">
      <div class="module-wrapper">
        <div class="module-blocks">
          <div class="module">
            <img src="@/assets/android.svg" alt="" />
          </div>
          <div class="module router">
            <img src="@/assets/rx_ic_route2.svg" alt="" />
          </div>
          <div class="module">
            <img src="@/assets/rx_site_reddit.svg" alt="" />
          </div>
          <WavyBackground
            class="waveContainer"
            waveWidth="1.2"
            blur="0"
            speed="fast"
            waveOpacity="1"
            :animate="false"
          ></WavyBackground>
        </div>
      </div>
      <p class="profile-name">Untitle profile</p>
    </div>
    <div class="profile-wrapper">
      <div class="module-wrapper">
        <div class="module-blocks">
          <div class="module">
            <img src="@/assets/android.svg" alt="" />
          </div>
          <div class="module">
            <img src="@/assets/rx_site_facebook.svg" alt="" />
          </div>
          <WavyBackground
            class="waveContainer"
            waveWidth="1.2"
            blur="0"
            speed="fast"
            waveOpacity="1"
            :animate="true"
          ></WavyBackground>
        </div>
      </div>
      <p class="profile-name">Untitle profile</p>
    </div>
  </div>
</template>

<script>
import WavyBackground from "@/components/WavyBackground.vue";

export default {
  components: {
    WavyBackground,
  },
};
</script>

<style>
.module-blocks {
  display: flex;
  align-items: center;
  width: 124px;
  justify-content: space-between;
}
.waveContainer {
  position: absolute;
  z-index: 0;
  width: 100px;
  height: 24px;
  left: 12px;
}
.module {
  position: relative;
  z-index: 1;
  width: 24px;
  height: 24px;
  display: flex;
  padding: 3.5px;
  justify-content: center;
  align-items: center;
  gap: var(--spacing-sm, 4px);

  border-radius: 4px;
  border: 0.5px solid var(--Colors-Border-border-action-secondary, #c7cdd1);
  background: var(--Colors-Background-bg-action-secondary, #fff);
  box-shadow: 0px 4px 4px -1px rgba(0, 0, 0, 0.02),
    0px 1px 1px 0px rgba(0, 0, 0, 0.06);
  &.router {
    background: rgb(255, 255, 255);
    background: linear-gradient(
      90deg,
      rgba(255, 255, 255, 0) 0%,
      rgba(255, 255, 255, 1) 15%,
      rgba(255, 255, 255, 1) 85%,
      rgba(255, 255, 255, 0) 100%
    );
    border: 0 none;
    box-shadow: none;
    img {
      opacity: 0.3;
    }
  }
}
.module-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
}
.profile-wrapper {
  position: relative;
  padding: 16px 0;
  display: flex;
  align-items: center;
  gap: 24px;
  .profile-name {
    width: 240px;
    font-weight: 500;
  }
}
.profile-list {
  display: flex;
  flex-direction: column;
  height: 100vh;
  justify-content: center;
  align-items: center;
}
.dashline {
  width: 104px;
  position: absolute;
  border-bottom: 1px dashed rgb(212, 212, 212);
}
</style>
