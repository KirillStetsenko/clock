<template>
  <div class="analog">
    <div class="dial">
      <div class="center"></div>
      <div class="digits">
        <div class="digit one">I</div>
        <div class="digit two">II</div>
        <div class="digit three corner">III</div>
        <div class="digit four">IV</div>
        <div class="digit five">V</div>
        <div class="digit six corner">VI</div>
        <div class="digit seven">VII</div>
        <div class="digit eight">VIII</div>
        <div class="digit nine corner">IX</div>
        <div class="digit ten">X</div>
        <div class="digit eleven">XI</div>
        <div class="digit twelve corner">XII</div>
      </div>
      <div class="hourHand" :style="{ transform: `rotate(${hoursDeg})` }"></div>
      <div
        class="minuteHand"
        :style="{ transform: `rotate(${minutesDeg})` }"
      ></div>
      <div
        class="secondHand"
        :style="{ transform: `rotate(${secondsDeg})` }"
      ></div>
    </div>
  </div>
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

  computed: {
    hoursDeg() {
      return (360 / 24) * this.hours + "deg";
    },

    minutesDeg() {
      return (360 / 60) * this.minutes + "deg";
    },

    secondsDeg() {
      return (360 / 60) * this.seconds + "deg";
    },
  },

  methods: {
    getCurrentTime() {
      const time = new Date();

      this.hours = String(time.getHours()).padStart(2, 0);
      this.minutes = String(time.getMinutes()).padStart(2, 0);
      this.seconds = String(time.getSeconds()).padStart(2, 0);
    },
  },

  mounted() {
    setInterval(() => {
      this.getCurrentTime();
    }, 1000);
  },
};
</script>

<style lang="scss" scoped>
.analog {
  text-align: center;

  .dial {
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 500px;
    height: 500px;
    border-radius: 50%;
    background-image: url("../assets/background/bg5.jpg");
    background-position: center center;
    background-size: cover;
    border: 1px solid rgb(255, 255, 255);

    .digits {
      position: absolute;
      width: 100%;
      height: 100%;
      display: flex;
      justify-content: center;
      align-items: center;

      .digit {
        position: absolute;
        height: 250px;
        text-align: center;
        font-weight: 200;
        font-size: 50px;
        transform-origin: center;
      }

      .corner {
        color: rgb(236, 255, 130);
        font-size: 80px;
        font-weight: 300;
      }

      .one {
        transform: rotate(30deg) translateY(-120px);
      }

      .two {
        transform: rotate(60deg) translateY(-120px);
      }

      .three {
        transform: rotate(90deg) translateY(-120px);
      }

      .four {
        transform: rotate(120deg) translateY(-120px);
      }

      .five {
        transform: rotate(150deg) translateY(-120px);
      }

      .six {
        transform: rotate(180deg) translateY(-120px);
      }

      .seven {
        transform: rotate(210deg) translateY(-120px);
      }

      .eight {
        transform: rotate(240deg) translateY(-120px);
      }

      .nine {
        transform: rotate(270deg) translateY(-120px);
      }

      .ten {
        transform: rotate(300deg) translateY(-120px);
      }

      .eleven {
        transform: rotate(330deg) translateY(-120px);
      }

      .twelve {
        transform: rotate(360deg) translateY(-120px);
      }
    }

    .center {
      position: absolute;
      width: 20px;
      height: 20px;
      z-index: 10;
      border-radius: 50%;
      background: rgb(255, 255, 255);
      border: 1px solid #000;
    }

    .hourHand,
    .minuteHand,
    .secondHand {
      position: absolute;
      bottom: 50%;
      transform-origin: 50% 100%;
    }

    .hourHand {
      width: 5px;
      height: 120px;
      background: white;
      border: 1px solid black;
    }

    .minuteHand {
      width: 5px;
      height: 160px;
      background: white;
      border: 1px solid black;
    }

    .secondHand {
      width: 2px;
      height: 180px;
      background: red;
      border: 1px solid black;
    }
  }
}
</style>
