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
      var source = audioCtx.createMediaStreamSource(this.stream);
      const audioMotion = new AudioMotionAnalyzer(
        document.getElementById("container"),
        this.options
      );
      let sourceMic = audioMotion.audioCtx.createMediaStreamSource(this.stream);
      sourceMic.connect(audioMotion.analyzer);
    }
  }
};
</script>

<style>
</style>