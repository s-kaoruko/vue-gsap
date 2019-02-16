<template>
  <div class="circle">
    <div class="box">
      <div class="green" :style="style"></div>
    </div>
  </div>
</template>
<script>
export default {
  created() {
    let angle = 0;
    setInterval(() => {
      this.style = this.position(++angle);
    }, 20);
  },
  data() {
    return {
      style: null
    };
  },
  methods: {
    position(angle) {
      const radius = 150;
      const x1 = -40;
      const y1 = -40;
      const x2 = x1 + radius + radius * Math.cos(angle * (Math.PI / 180));
      const y2 = y1 + radius + radius * Math.sin(angle * (Math.PI / 180));
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
  display: flex;
  align-items: center;
  justify-content: center;
}
.box {
  flex: 0 0 auto;
  width: 300px;
  height: 300px;
  position: relative;
}
.green {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  background: $green;
  position: absolute;
}
</style>
