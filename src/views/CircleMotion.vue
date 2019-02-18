<template>
  <div class="circle">
    <div class="button-box">
      <button type="button" ref="play">play</button>
      <button type="button" ref="pause">pause</button>
    </div>
    <div class="circle-box">
      <div class="box">
        <div class="box-item _red" ref="red1" :style="position1"></div>
        <div class="box-item _red" ref="red2" :style="position2"></div>
        <div class="box-item _red" ref="red3" :style="position3"></div>
        <div class="box-item _red" ref="red4" :style="position4"></div>
        <div class="box-item _red" ref="red5" :style="position5"></div>
        <div class="box-item _red" ref="red6" :style="position6"></div>

        <div class="box-item _blue" ref="blue1" :style="position1"></div>
        <div class="box-item _blue" ref="blue2" :style="position2"></div>
        <div class="box-item _blue" ref="blue3" :style="position3"></div>
        <div class="box-item _blue" ref="blue4" :style="position4"></div>
        <div class="box-item _blue" ref="blue5" :style="position5"></div>
        <div class="box-item _blue" ref="blue6" :style="position6"></div>

        <div class="box-item _green" ref="green1" :style="position1"></div>
        <div class="box-item _green" ref="green2" :style="position2"></div>
        <div class="box-item _green" ref="green3" :style="position3"></div>
        <div class="box-item _green" ref="green4" :style="position4"></div>
        <div class="box-item _green" ref="green5" :style="position5"></div>
        <div class="box-item _green" ref="green6" :style="position6"></div>
      </div>
    </div>
  </div>
</template>
<script>
import { TweenMax, Power0 } from "gsap";
export default {
  created() {
    let radius1 = 150;
    let position1 = [130, 130];
    this.position1 = this.getPosition(270, radius1, position1);
    this.position2 = this.getPosition(30, radius1, position1);
    this.position3 = this.getPosition(150, radius1, position1);

    this.position4 = this.getPosition(90, radius1, position1);
    this.position5 = this.getPosition(210, radius1, position1);
    this.position6 = this.getPosition(330, radius1, position1);

    let afterRadius1 = 50;
    let afterPosition1 = [130, 130];
    this.afterPosition1 = this.getPosition(
      270,
      afterRadius1,
      afterPosition1,
      true
    );
    this.afterPosition2 = this.getPosition(
      30,
      afterRadius1,
      afterPosition1,
      true
    );
    this.afterPosition3 = this.getPosition(
      150,
      afterRadius1,
      afterPosition1,
      true
    );

    this.afterPosition4 = this.getPosition(
      90,
      afterRadius1,
      afterPosition1,
      true
    );
    this.afterPosition5 = this.getPosition(
      210,
      afterRadius1,
      afterPosition1,
      true
    );
    this.afterPosition6 = this.getPosition(
      330,
      afterRadius1,
      afterPosition1,
      true
    );
  },
  mounted() {
    let animateGreen1,
      animateGreen2,
      animateGreen3,
      animateGreen4,
      animateGreen5,
      animateGreen6,
      animateRed1,
      animateRed2,
      animateRed3,
      animateRed4,
      animateRed5,
      animateRed6,
      animateBlue1,
      animateBlue2,
      animateBlue3,
      animateBlue4,
      animateBlue5,
      animateBlue6;

    this.$refs.play.addEventListener("click", () => {
      if (this.hadPause) {
        animateGreen1.play();
        animateGreen2.play();
        animateGreen3.play();
        animateGreen4.play();
        animateGreen5.play();
        animateGreen6.play();
        animateRed1.play();
        animateRed2.play();
        animateRed3.play();
        animateRed4.play();
        animateRed5.play();
        animateRed6.play();
        animateBlue1.play();
        animateBlue2.play();
        animateBlue3.play();
        animateBlue4.play();
        animateBlue5.play();
        animateBlue6.play();
      } else {
        animateGreen1 = TweenMax.to(this.$refs.green1, 1.2, this.afterPosition1)
          .repeat(-1)
          .yoyo(true);
        animateGreen2 = TweenMax.to(this.$refs.green2, 1.2, this.afterPosition2)
          .repeat(-1)
          .yoyo(true);
        animateGreen3 = TweenMax.to(this.$refs.green3, 1.2, this.afterPosition3)
          .repeat(-1)
          .yoyo(true);
        animateGreen4 = TweenMax.to(this.$refs.green4, 1.2, this.afterPosition4)
          .repeat(-1)
          .yoyo(true)
          .delay(1.2);
        animateGreen5 = TweenMax.to(this.$refs.green5, 1.2, this.afterPosition5)
          .repeat(-1)
          .yoyo(true)
          .delay(1.2);
        animateGreen6 = TweenMax.to(this.$refs.green6, 1.2, this.afterPosition6)
          .repeat(-1)
          .yoyo(true)
          .delay(1.2);

        animateRed1 = TweenMax.to(this.$refs.red1, 1.2, this.afterPosition1)
          .repeat(-1)
          .yoyo(true)
          .delay(0.8);
        animateRed2 = TweenMax.to(this.$refs.red2, 1.2, this.afterPosition2)
          .repeat(-1)
          .yoyo(true)
          .delay(0.8);
        animateRed3 = TweenMax.to(this.$refs.red3, 1.2, this.afterPosition3)
          .repeat(-1)
          .yoyo(true)
          .delay(0.8);
        animateRed4 = TweenMax.to(this.$refs.red4, 1.2, this.afterPosition4)
          .repeat(-1)
          .yoyo(true)
          .delay(2.0);
        animateRed5 = TweenMax.to(this.$refs.red5, 1.2, this.afterPosition5)
          .repeat(-1)
          .yoyo(true)
          .delay(2.0);
        animateRed6 = TweenMax.to(this.$refs.red6, 1.2, this.afterPosition6)
          .repeat(-1)
          .yoyo(true)
          .delay(2.0);

        animateBlue1 = TweenMax.to(this.$refs.blue1, 1.2, this.afterPosition1)
          .repeat(-1)
          .yoyo(true)
          .delay(1.6);
        animateBlue2 = TweenMax.to(this.$refs.blue2, 1.2, this.afterPosition2)
          .repeat(-1)
          .yoyo(true)
          .delay(1.6);
        animateBlue3 = TweenMax.to(this.$refs.blue3, 1.2, this.afterPosition3)
          .repeat(-1)
          .yoyo(true)
          .delay(1.6);
        animateBlue4 = TweenMax.to(this.$refs.blue4, 1.2, this.afterPosition4)
          .repeat(-1)
          .yoyo(true)
          .delay(2.8);
        animateBlue5 = TweenMax.to(this.$refs.blue5, 1.2, this.afterPosition5)
          .repeat(-1)
          .yoyo(true)
          .delay(2.8);
        animateBlue6 = TweenMax.to(this.$refs.blue6, 1.2, this.afterPosition6)
          .repeat(-1)
          .yoyo(true)
          .delay(2.8);
      }
    });
    this.$refs.pause.addEventListener("click", () => {
      animateGreen1.pause();
      animateGreen2.pause();
      animateGreen3.pause();
      animateGreen4.pause();
      animateGreen5.pause();
      animateGreen6.pause();
      animateRed1.pause();
      animateRed2.pause();
      animateRed3.pause();
      animateRed4.pause();
      animateRed5.pause();
      animateRed6.pause();
      animateBlue1.pause();
      animateBlue2.pause();
      animateBlue3.pause();
      animateBlue4.pause();
      animateBlue5.pause();
      animateBlue6.pause();
      this.hadPause = true;
    });
  },
  data() {
    return {
      position1: null,
      position2: null,
      position3: null,
      position4: null,
      position5: null,
      position6: null,
      afterPosition1: null,
      afterPosition2: null,
      afterPosition3: null,
      afterPosition4: null,
      afterPosition5: null,
      afterPosition6: null,
      hadPause: false
    };
  },
  methods: {
    /**
     * @param {number} angle - 角度
     * @param {number} radius - 基準ボックスのwidth/2
     * @param {number[]} startPosition
     */
    getPosition(angle, radius, startPosition, isAfter = false) {
      const x1 = startPosition[0];
      const y1 = startPosition[1];
      const x2 = x1 + radius * Math.cos(angle * (Math.PI / 180));
      const y2 = y1 + radius * Math.sin(angle * (Math.PI / 180));
      return {
        top: y2 + "px",
        left: x2 + "px",
        opacity: isAfter ? "0.5" : "1",
        transform: isAfter ? "scale(1)" : "scale(1.5)",
        ease: Power0.easeNone
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
  &-item {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    position: absolute;
    z-index: 0;
    opacity: 0.5;
    transform-origin: center;
    &._green {
      background: $green;
    }
    &._red {
      background: $red;
    }
    &._blue {
      background: $blue;
    }
  }
}
</style>
