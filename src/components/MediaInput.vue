<template>
  <v-container>
  <v-select
          :items="types"
          item-text="name"
          item-value="value"
          label="Outlined style"
          outlined
          v-model="selectedType"
          :canv-width="canWidth"
          :can-height="canHeight"
          :radius="radius"
        ></v-select>
  <audio ref="player" controls />
  <av-media :media="media" :type="selectedType"/>
  <h2>Line</h2>
  <av-line
       :line-width="2"
       line-color="lime"
       :audio-src="src"
       :cors-anonym="cors"
     ></av-line>
     <h2>Waveform</h2>
     <av-waveform
      :audio-src="src"
      :cors-anonym="cors"
    ></av-waveform>
    <h2>Circle (Glowing effect to be added)</h2>
    <av-circle
  :outline-width="0"
  :progress-width="5"
  :outline-meter-space="5"
  :cors-anonym="cors"
  :playtime="true"
  playtime-font="18px Monaco"
  :audio-src="src"
></av-circle>
<h2> Bars </h2>

<av-bars
      caps-color="#FFF"
      :bar-color="['#f00', '#ff0', '#0f0']"
      canv-fill-color="#000"
      :caps-height="2"
      :audio-src="src"
      :cors-anonym="cors"
    ></av-bars>
</v-container>
</template>
<script>
export default {
    name: 'MediaInput',
    data() {
        return {
            media: null,
            types: [
              {
                name: 'Waveform',
                value: 'wform'
              },
              {
                name: 'Circle',
                value: 'circle'
              },
              {
                name: 'Frequency',
                value: 'frequ'
              }
            ],
            selectedType: 'frequ',
            radius: 10,
            canWidth: 600,
            canHeight: 600,
            cors: true,
            src: 'https://www.podtrac.com/pts/redirect.mp3/traffic.megaphone.fm/ADV4942283554.mp3?updated=1612548275'
        }
    },
    mounted () {
      const constraints = { audio: true, video: false }
      navigator.mediaDevices.getUserMedia(constraints).
        then(media => {
          this.media = media
          this.$refs.player.srcObject = media
        })
    }
}
</script>
