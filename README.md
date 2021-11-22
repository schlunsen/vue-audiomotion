# vue-audiomotion-analyzer

[![npm (scoped with tag)](https://img.shields.io/npm/v/vue-audiomotion/latest.svg?style=flat-square)](https://npmjs.com/package/vue-audiomotion)
[![npm](https://img.shields.io/npm/dt/vue-audiomotion.svg?style=flat-square)](https://npmjs.com/package/vue-audiomotion)
[![js-standard-style](https://img.shields.io/badge/code_style-standard-brightgreen.svg?style=flat-square)](http://standardjs.com)

Wrapper for the awesome [audiomotion-analyzer](https://www.npmjs.com/package/audiomotion-analyzer)

## Project setup

```
npm install vue-audiomotion
```

## Usage

Add the comonent

```html
<script>
  import AudioMotionAnalyzer from "audiomotion-analyzer";

  export default {
    data() {
      return {
        options: {
            audioCtx: AudioContext object,
            barSpace: number (2),
            fftSize: number (8192),
            fillAlpha: number (1),
            gradient: string ('classic'),
            height: number,
            lineWidth: number (0),
            loRes: boolean (false),
            lumiBars: boolean (false),
            maxDecibels: number (-25),
            maxFreq: number (22000),
            minDecibels: number (-85),
            minFreq: number (20),
            mode: number (0),
            onCanvasDraw: function,
            onCanvasResize: function,
            reflexAlpha: number (0.15),
            reflexFit: boolean (true),
            reflexRatio: number (0),
            showBgColor: boolean (true),
            showFPS: boolean (false),
            showLeds: boolean (false),
            showPeaks: boolean (true),
            showScale: boolean (true),
            smoothing: number (0.5),
            source: HTMLMediaElement,
            start: boolean (true),
            width: number
      },
      customGradients: [
        {
          name: "newGradient",
          options: {
            bgColor: '#fff', // background color (required)
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
    },
    mounted() {
      navigator.mediaDevices
        .getUserMedia({
          video: false,
          audio: true
        })
        .then(stream => {
          this.stream = stream;
        })
        .catch(err => {});

        // Access AudioMotionAnalyzer obj
        // See https://www.npmjs.com/package/audiomotion-analyzer#methods for available methods
        let audioMotionAnalyzer = this.$refs.audioMotion.getAudioMotion()
        
    }
  };
</script>
```

```html
<AudioMotion
  ref="audioMotion"
  :stream="stream"
  :options="options"
  :customGradients="customGradients"
></AudioMotion>
```

## Thanks

Big thanks to [Hivanna](https://github.com/hvianna) for creating AudioMotion

Checkout the [demo page](https://audiomotion.me/public/)

## License

[MIT License](./LICENSE)

Copyright (c) Rasmus Schlunsen
