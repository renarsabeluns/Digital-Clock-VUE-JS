<template>
<div class="clock">
  <div class="time">
    <span>{{time}}</span>
  </div>
</div>
</template>

<script>
import { ref } from 'vue'

export default {
  name: 'App',
  setup(){
    let now = new Date(); // I wanted to add ref() here but I noticed that const time will be changing not the variable now
    const time = ref(now.toLocaleTimeString("lv-LV"));

    setInterval(() => {
      now = new Date();
      time.value = now.toLocaleTimeString("lv-LV"); // A simple use of the method setInterval to add time to this clock :D
    }, 1000);

    return {
      time,
    };

  }

}
</script>

<style>

  html,
  body {
     height: 100%;
     overflow:hidden;
  }
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: auto;
  align-items: center;
  display: flex;
  justify-content: center;
  height: 100%;
}

.time{
  font-size:100px;
}
</style>
