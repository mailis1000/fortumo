<template>
  <div id="app">
    <img src="./assets/fortumo-logo.png">
    <div class="chart-cont">
      <router-view/>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
body {
  margin: 0;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #fff;
  background-color: #221f1f;
  width: 100vw;
  margin: 0;
  height: 100vh;
  position: relative;
}
img {
  margin-top: 3vh;
  margin-bottom: 1vh;
}
canvas {
  min-height: 80vh;
}
</style>
