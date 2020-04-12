# vue-audiomotion-analyzer

Wrapper for the awesome https://www.npmjs.com/package/audiomotion-analyzer

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
      };
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
    }
  };
</script>
```

```html
<AudioMotion :stream="stream"></AudioMotion>
```

## License

[MIT License](./LICENSE)

Copyright (c) Rasmus Schlunsen




