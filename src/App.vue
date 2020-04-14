<template>
  <div id="app">
    <AudioMotion
      ref="audioMotion"
      :stream="stream"
      :options="options"
      :customGradients="customGradients"
    />
  </div>
</template>

<script>
import AudioMotion from "./components/AudioMotion.vue";

export default {
  name: "App",
  data() {
    return {
      stream: null,
      options: {
        barSpace: 100,
        lineWidth: 100,
        gradient: "customGradient",
        lumiBars: true,
        showBgColor: true,
        showScale: false,
        showLeds: false
      },
      customGradients: [
        {
          name: "customGradient",
          options: {
            bgColor: "#fff", // background color (required)
            dir: "h", // add this to create a horizontal gradient (optional)
            colorStops: [
              // list your gradient colors in this array (at least 2 entries are required)
              "yellow", // colors may be defined in any CSS valid format
              { pos: 0.6, color: "#ff0" }, // use an object to adjust the position (0 to 1) of a color
              "hsl( 0, 100%, 50% )" // colors may be defined in any CSS valid format
            ]
          }
        }
      ]
    };
  },
  async mounted() {
    await navigator.mediaDevices
      .getUserMedia({
        video: false,
        audio: true
      })
      .then(stream => {
        this.stream = stream;
      })
      .catch(err => {
        console.error(err);
      });

    // Access audiomotion object

    console.info(this.$refs.audioMotion.getAudioMotion());
  },
  components: {
    AudioMotion
  }
};
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
