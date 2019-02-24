<template>
  <div class="circle">
    <button type="button" ref="play">play</button>
    <button type="button" ref="pause">pause</button>

    <div class="circle-box">
      <div class="box">
        <div class="box-item _red" ref="circle" :style="style1"></div>
      </div>
    </div>
  </div>
</template>

<script>
import { TimelineMax, Power0 } from "gsap";
export default {
  mounted() {
    let timeline;
    this.$refs.play.addEventListener("click", () => {
      if (this.hadPause) {
        timeline.play();
      } else {
        timeline = new TimelineMax({ repeat: -1 });
        timeline
          .to(this.$refs.circle, 0.6, this.style2)
          .to(this.$refs.circle, 0.6, this.style3)
          .to(this.$refs.circle, 0.6, this.style4)
          .to(this.$refs.circle, 0.6, this.style1);
      }
    });
    this.$refs.pause.addEventListener("click", () => {
      timeline.pause();
      this.hadPause = true;
    });
  },
  data() {
    return {
      style1: {
        top: "20px",
        transform: "scale(2)",
        // TODO: 円周をぐるぐる回ってる感がないのはeasingのせいなのか
        // ease: Circ.easeIn
        ease: Power0.easeNone
      },
      style2: {
        top: "110px",
        transform: "scale(4)",
        // ease: Circ.easeOut
        ease: Power0.easeNone
      },
      style3: {
        top: "240px",
        transform: "scale(2)",
        // ease: Circ.easeIn
        ease: Power0.easeNone
      },
      style4: {
        top: "110px",
        transform: "scale(1)",
        // ease: Circ.easeOut
        ease: Power0.easeNone
      },
      hadPause: false
    };
  }
};
</script>

<style lang="scss" scoped>
$blue: #2348f3;
.circle {
  width: 100%;
  height: 100vh;
  background: #000000;
  position: relative;
  &-box {
    position: absolute;
    top: calc(50% - 150px);
    left: calc(50% - 150px);
  }
}
.box {
  flex: 0 0 auto;
  width: 300px;
  height: 300px;
  box-sizing: border-box;
  position: relative;
  // border: 1px solid #fff;
  padding: 20px;
  &-item {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    position: absolute;
    left: calc(50% - 20px);
    z-index: 0;
    transform-origin: center;
    background: $blue;
  }
}
</style>
