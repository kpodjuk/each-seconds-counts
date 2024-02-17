<template>
  <div id="app">
    <div id="background" :style="{ backgroundColor: bgColor, transition: 'background-color 500ms' }"></div>
    <div id="clock" style="color: white; text-shadow: 0px 0px 50px rgba(0, 0, 0, 0.8);">{{ currentTime }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      bgColor: "",
      currentTime: "",
    };
  },
  mounted() {
    this.changeBackgroundColor();
    this.updateClock();
    setInterval(this.changeBackgroundColor, 1000);
    setInterval(this.updateClock, 1000);
  },
  methods: {
    changeBackgroundColor() {
      const randomColor = "#" + Math.floor(Math.random() * 16777215).toString(16);
      this.bgColor = randomColor;
    },
    updateClock() {
      const now = new Date();
      const hh = now.getHours().toString().padStart(2, "0");
      const mm = now.getMinutes().toString().padStart(2, "0");
      const ss = now.getSeconds().toString().padStart(2, "0");
      this.currentTime = `${hh}:${mm}:${ss}`;
    },
  },
};
</script>

<style>
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  font-family: Arial, sans-serif;
}

#background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

#clock {
  font-size: 10rem;
  z-index: 1;
  text-align: center;
}
</style>
