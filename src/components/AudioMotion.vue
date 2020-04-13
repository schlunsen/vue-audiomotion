<template>
  <div :ref="'audioMotion-' + this._uid"></div>
</template>
<script>
import AudioMotionAnalyzer from "audiomotion-analyzer";

export default {
  props: ["stream", "options"],
  watch: {
    stream() {
      if (this.stream && this.stream.getAudioTracks().length) {
        var audioCtx = new AudioContext();
        var source = audioCtx.createMediaStreamSource(this.stream);
        const audioMotion = new AudioMotionAnalyzer(
          this.$refs["audioMotion" + this._uid],
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