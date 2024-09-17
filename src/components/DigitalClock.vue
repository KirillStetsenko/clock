<template>
  <main class="main">
    <div class="digital">{{ hours }}:{{ minutes }}:{{ seconds }}</div>
  </main>
</template>

<script>
export default {
  data() {
    return {
      hours: null,
      minutes: null,
      seconds: null,
    };
  },

  methods: {
    getTime() {
      const time = new Date();

      this.hours = String(time.getHours()).padStart(2, 0);
      this.minutes = String(time.getMinutes()).padStart(2, 0);
      this.seconds = String(time.getSeconds()).padStart(2, 0);
    },
  },

  mounted() {
    setInterval(() => {
      this.getTime();
    }, 1000);
  },
};
</script>

<style lang="scss" scoped>
.digital {
  font-size: 200px;
}
</style>
