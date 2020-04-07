<template>
  <div class="App">
    <video ref="videoPlayer" class="video-js"></video>
  </div>
</template>

<script>
import videojs from 'video.js';

export default {
  name: "VideoPlayer",
  props: {
    options: {
      type: Object,
      default() {
          return {};
      }
    }
  },
  data() {
    return {
      player: null
    }
  },
  mounted() {
    // add ByteArk Lighthouse middleware to videojs
    videojs.use('*', window.ByteArkLighthouse.middleware);
    
    this.player = videojs(this.$refs.videoPlayer, this.options, function onPlayerReady() {
      console.log('onPlayerReady', this);
    });

    // init Byteark Lighthouse
    window.ByteArkLighthouse.init(this.player, {
      projectId: 'videojs-byteark-lighthouse-uta',
      // TODO: don't forget to remove debug when deploy in production
      debug: true,
    });
  },
  beforeDestroy() {
    if (this.player) {
      this.player.dispose();
    }

    window.ByteArkLighthouse.destroy();
  },
  methods: {
    src(source) {
      if (this.player) {
        this.player.src(source);
      }
    }
  }
}
</script>