<template>
  <div class="circle">
    <button type="button" ref="play">play</button>
    <button type="button" ref="pause">pause</button>

    <div class="circle-box">
      <div class="box">
        <div class="box-item _red" ref="circle" :style="perspective1"></div>
      </div>
    </div>
  </div>
</template>

<script>
import { TimelineMax, Circ } from "gsap";
export default {
  mounted() {
    let perspective;
    this.$refs.play.addEventListener("click", () => {
      if (this.hadPause) {
        perspective.play();
      } else {
        perspective = new TimelineMax({ repeat: -1 });
        perspective
          .to(this.$refs.circle, 1.0, this.perspective2)
          .to(this.$refs.circle, 1.0, this.perspective1);
      }
    });
    this.$refs.pause.addEventListener("click", () => {
      perspective.pause();
      this.hadPause = true;
    });
  },
  data() {
    return {
      perspective1: {
        transform: "perspective(100px) translateZ(0px)",
        ease: Circ.easeIn
      },
      perspective2: {
        transform: "perspective(100px) translateZ(50px)",
        ease: Circ.easeOut
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
    left: calc(50% - 150px);
  }
}
.box {
  flex: 0 0 auto;
  width: 300px;
  height: 300px;
  box-sizing: border-box;
  position: relative;
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
