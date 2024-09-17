<template>
  <main class="main">
    <div class="buttonsBlock">
      <button class="btn" @click="this.toggleClock = !this.toggleClock">
        Toggle Clock
      </button>
    </div>
    <div class="clock">
      <digital-clock :style="{ display: this.toggleClock ? 'none' : '' }" />
      <analog-clock :style="{ display: this.toggleClock ? '' : 'none' }" />
    </div>
  </main>
</template>

<script>
import AnalogClock from "./components/AnalogClock.vue";
import DigitalClock from "./components/DigitalClock.vue";

export default {
  components: { AnalogClock, DigitalClock },

  data() {
    return {
      toggleClock: true,
    };
  },
};
</script>

<style lang="scss" scoped>
.main {
  text-align: center;
  height: 100vh;

  .buttonsBlock {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 20px;
    gap: 30px;

    .btn {
      width: 70px;
      height: 70px;

      display: flex;
      justify-content: center;
      align-items: center;
      border-radius: 50%;
      border: 1px solid black;
      background: #444;
      color: white;
      transition: 0.3s;

      &:hover {
        border: 1px solid white;
      }
    }
  }

  .clock {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 30px;
  }
}
</style>
