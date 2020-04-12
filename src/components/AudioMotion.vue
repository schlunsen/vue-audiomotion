<template>
  <div id="container"></div>
</template>
<script>
import AudioMotionAnalyzer from "audiomotion-analyzer";

export default {
  props: ["stream", "options"],
  watch: {
    stream() {
      var audioCtx = new AudioContext();
      console.info(this.stream);
      var source = audioCtx.createMediaStreamSource(this.stream);
      const audioMotion = new AudioMotionAnalyzer(
        document.getElementById("container"),
        {}
      );

      let sourceMic = audioMotion.audioCtx.createMediaStreamSource(this.stream);
      console.info(sourceMic, "Source mic");
      sourceMic.connect(audioMotion.analyzer);
    }
  }
};
</script>

<style>
</style>