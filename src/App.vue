<template>
  <div id="app">
    <AudioMotion :stream="stream" :options="options" />
    
  </div>
</template>

<script>
import AudioMotion from './components/AudioMotion.vue'

export default {
  name: 'App',
  data() {
    return {
      stream: null,
      options: {
        barSpace: 100,
        lineWidth: 100,
        gradient: 'prism',
        lumiBars: true
      }
    }
  },
  async mounted() {
    return await navigator.mediaDevices
        .getUserMedia({
          video: false,
          audio: true,
        })
        .then(stream => {
          this.stream = stream
        })
        .catch((err) => {
          console.error(err);
        });
  },
  components: {
    AudioMotion
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
