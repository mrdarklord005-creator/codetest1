<template>
  <div id="app">
    <div class="container">
<Home />
    </div>
    
  </div>
</template>

<script>
import Home from './components/Home.vue'

export default {
  name: 'App',
  components: {
    Home
  }
}
</script>

<style>
.container {
  width: 100%;
   box-sizing: border-box;
  text-align: center;
  justify-content: center;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  position: relative;
  min-height: 100vh;
  margin: 0 !important;
}

#app::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-image: url('/src/assets/gold4.png'); 
  background-size: cover;
  background-position: center;
  filter: blur(1px); 
  z-index: -1;
}

body {
  font-family: Arial, sans-serif;
  background-color: #111;
  margin: 0 !important;
  padding: 0 !important;
  overflow-y: auto; /* ให้สามารถเลื่อนแนวตั้งได้ */
  height: 100%;
}
</style>
