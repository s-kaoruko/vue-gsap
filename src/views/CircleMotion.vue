<template>
  <div class="circle">
    <div class="circle-box">
      <div class="box">
        <div class="box-item _green" ref="green1" :style="position1"></div>
        <div class="box-item _green" ref="green2" :style="position2"></div>
        <div class="box-item _green" ref="green3" :style="position3"></div>
      </div>
      <div class="box _after"></div>
    </div>
    <button type="button" ref="play">play</button>
    <button type="button" ref="pause">pause</button>
  </div>
</template>
<script>
import { TweenMax } from "gsap";
export default {
  created() {
    let radius1 = 150;
    let position1 = [130, 130];
    this.position1 = this.getPosition(270, radius1, position1);
    this.position2 = this.getPosition(30, radius1, position1);
    this.position3 = this.getPosition(150, radius1, position1);

    let afterRadius1 = 50;
    let afterPosition1 = [130, 130];
    this.afterPosition1 = this.getPosition(270, afterRadius1, afterPosition1);
    this.afterPosition2 = this.getPosition(30, afterRadius1, afterPosition1);
    this.afterPosition3 = this.getPosition(150, afterRadius1, afterPosition1);
  },
  mounted() {
    let animateGreen1, animateGreen2, animateGreen3;
    this.$refs.play.addEventListener("click", () => {
      if (this.hadPause) {
        animateGreen1.play();
        animateGreen2.play();
        animateGreen3.play();
      } else {
        animateGreen1 = TweenMax.to(this.$refs.green1, 1, this.afterPosition1)
          .repeat(-1)
          .yoyo(true);
        animateGreen2 = TweenMax.to(this.$refs.green2, 1, this.afterPosition2)
          .repeat(-1)
          .yoyo(true);
        animateGreen3 = TweenMax.to(this.$refs.green3, 1, this.afterPosition3)
          .repeat(-1)
          .yoyo(true);
      }
    });
    this.$refs.pause.addEventListener("click", () => {
      animateGreen1.pause();
      animateGreen2.pause();
      animateGreen3.pause();
      this.hadPause = true;
    });
  },
  data() {
    return {
      position1: null,
      position2: null,
      position3: null,
      afterPosition1: null,
      afterPosition2: null,
      afterPosition3: null,
      hadPause: false
    };
  },
  methods: {
    /**
     * @param {number} angle - 角度
     * @param {number} radius - 基準ボックスのwidth/2
     * @param {number[]} startPosition
     */
    getPosition(angle, radius, startPosition) {
      const x1 = startPosition[0];
      const y1 = startPosition[1];
      const x2 = x1 + radius * Math.cos(angle * (Math.PI / 180));
      const y2 = y1 + radius * Math.sin(angle * (Math.PI / 180));
      return {
        top: y2 + "px",
        left: x2 + "px"
      };
    }
  }
};
</script>
<style lang="scss" scoped>
$green: #7bea19;
$red: #e23d31;
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
  position: relative;
  border-radius: 50%;
  border: 1px solid #ccc;
  &._after {
    width: 100px;
    height: 100px;
    position: absolute;
    top: 100px;
    left: 100px;
    border-radius: 50%;
    border: 1px solid #ccc;
    opacity: 0.7;
  }
  &-item {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    position: absolute;
    &._green {
      background: $green;
    }
  }
}
</style>
