<template>
  <div ref="audioMotion"></div>
</template>
<script>
import AudioMotionAnalyzer from "audiomotion-analyzer";

export default {
  props: ["stream", "options"],
  mounted() {
    this.audioMotion = this.$refs.audioMotion
  },
  watch: {
    stream() {
      if (this.stream && this.stream.getAudioTracks().length) {
        var audioCtx = new AudioContext();
        var source = audioCtx.createMediaStreamSource(this.stream);
        const audioMotion = new AudioMotionAnalyzer(
          this.audioMotion,
          this.options
        );
        let sourceMic = audioMotion.audioCtx.createMediaStreamSource(
          this.stream
        );
        sourceMic.connect(audioMotion.analyzer);
      }
    }
  }
};
</script>

<style>
</style>