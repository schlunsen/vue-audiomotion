<template>
  <div ref="audioMotion"></div>
</template>
<script>
import AudioMotionAnalyzer from "audiomotion-analyzer";

export default {
  props: ["stream", "options", "customGradients"],
  data() {
    return {
      audioMotionObj: null
    };
  },
  mounted() {
    this.audioMotionElement = this.$refs.audioMotion;

  },
  watch: {
    stream() {
      if (this.stream && this.stream.getAudioTracks().length) {
        var audioCtx = new AudioContext();
        var source = audioCtx.createMediaStreamSource(this.stream);
        this.audioMotionObj = new AudioMotionAnalyzer(
          this.audioMotionElement
          //this.options
        );

        // Set extra options as custom gradients
        if (this.customGradients) {
          this.customGradients.forEach(gradientObj => {
            this.audioMotionObj.registerGradient(
              gradientObj.name,
              gradientObj.options
            );
          });

          this.audioMotionObj.setOptions(this.options);
        }

        let audioStream = this.audioMotionObj.audioCtx.createMediaStreamSource(
          this.stream
        );
        audioStream.connect(this.audioMotionObj.analyzer);
      }
    }
  },
  methods: {
    getAudioMotion() {
      return this.audioMotionObj;
    }
  }
};
</script>

<style>
</style>