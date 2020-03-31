<template>
  <div>
    <nav class="navbar sticky-top navbar-dark bg-dark">
      <a class="navbar-brand" href="#">ByteArk Lighthouse Video.js React Example</a>
    </nav>
    <div class="container-fluid pt-4">
      <div class="row">
        <div class="col-md-8">
          <form>
            <div class="form-group">
              <label>Select Video</label>
              <select class="form-control"
                @change="onSelectVideoIndex">
                <option value="0">#1 BIG BUCK BUNNY</option>
                <option value="1">#2 ByteArk</option>
              </select>
            </div>
          </form>
        </div>
      </div>
      <div class="row">
        <div class="col-md-8">
          <video-player ref="player" :options="videoOptions"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import VideoPlayer from "@/components/VideoPlayer.vue";
import 'video.js/dist/video-js.css';

const sources = [
  {
    videoId: 'RI2PimuHxDXw',
    title: 'BIG BUCK BUNNY',
    subtitle: 'Big buck bunny sample video',
    poster: '//qoder.byteark.com/images/video-frames/1/GU/cg/1GUcghrocmlz-large.jpg',
    src: '//inox-bhm9yr.cdn.byteark.com/video-objects/RI2PimuHxDXw/playlist.m3u8',
    type: 'application/x-mpegURL',
  },
  {
    videoId: 'Rqi1fj7fP130',
    title: 'ByteArk Promo Video',
    subtitle: 'ByteArk Promo sample video',
    poster: '//qoder.byteark.com/images/video-frames/1/J3/tm/1J3tmPOkPQYF-large.jpg',
    src: '//inox-bhm9yr.cdn.byteark.com/video-objects/Rqi1fj7fP130/playlist.m3u8',
    type: 'application/x-mpegURL',
  }
]

export default {
  name: 'App',
  components: {
    VideoPlayer
  },
  data() {
    return {
      videoOptions: {
        autoplay: true,
        controls: true,
        fluid: true,
        sources
      }
    }
  },
  methods: {
    onSelectVideoIndex(event) {
      this.$refs.player.src(sources[event.target.value]);
    }
  }
}
</script>

<style>
body {
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen',
    'Ubuntu', 'Cantarell', 'Fira Sans', 'Droid Sans', 'Helvetica Neue',
    sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

code {
  font-family: source-code-pro, Menlo, Monaco, Consolas, 'Courier New',
    monospace;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.navbar-brand {
  white-space: pre-wrap;
}
</style>
