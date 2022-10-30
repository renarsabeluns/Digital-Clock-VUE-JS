<template>
  <div class="clock">
    <div class="time">
      <span class="glow">{{time}}</span>
    </div>
    <div class="date">
     <span>{{date}}</span> 
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  name: 'App',
  setup() {
    let now = new Date(); // I wanted to add ref() here but I noticed that const time will be changing not the variable now
    const time = ref(now.toLocaleTimeString("lv-LV"));
    const date = now.toDateString("lv-LV");

    setInterval(() => {
      now = new Date();
      time.value = now.toLocaleTimeString("lv-LV"); // A simple use of the method setInterval to add time to this clock :D
    }, 1000);

    return {
      time,
      date
    };

  }

}
</script>

<style>
html,
body {
  height: 100%;
  overflow: hidden;
  background-color: black;
}

@font-face {
  font-family: 'digital-clock-font';
  color: #56c465;
  src: url('/public/digital-7.regular.ttf');
}

#app {
  font-family: 'digital-clock-font';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #56c465;;
  margin-top: auto;
  align-items: center;
  display: flex;
  justify-content: center;
  height: 100%;

}

.date {
  font-size: 60px;
  justify-content: space-between;

  text-shadow:

    0 0 42px rgb(60, 198, 76),
    0 0 82px rgb(60, 198, 76),
    0 0 92px rgb(60, 198, 76),
    0 0 102px rgb(60, 198, 76),
    0 0 151px rgb(60, 198, 76);

}


.time {
  font-size: 200px;
}

:root {
  --neon-text-color: darkgreen;
}



span {
  padding: 4rem 6rem 5.5rem;
  text-transform: uppercase;
  animation: flicker 2s infinite alternate;
  /* animation-delay: 60s; */
}



span:focus {
  outline: none;
}

/* Animate neon flicker */
@keyframes flicker {

  0%,
  19%,
  21%,
  23%,
  25%,
  54%,
  56%,
  100% {
    text-shadow: 
      -0.2rem -0.2rem 1rem darkgreen,
        0 0 0rem var(--neon-text-color),
        0 0 0rem var(--neon-text-color),
        0 0 1rem var(--neon-text-color),
        0 0 2rem var(--neon-text-color),
        0 0 3rem var(--neon-text-color);
  }

  20%,
  24%,
  55% {
    text-shadow: none;
  }
}
</style>
