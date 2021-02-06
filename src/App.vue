<template>
  <v-app>
    <v-app-bar
      app
      color="black"
      dark
    >
      <div class="d-flex align-center">
        <h1>B1 Audio Visualizer</h1>
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
        text
      >

      </v-btn>
    </v-app-bar>

    <v-main>
      <MediaInput/>
    </v-main>
  </v-app>
</template>

<script>
import MediaInput from './components/MediaInput';

export default {
  name: 'App',

  components: {
    MediaInput
  },

  data: () => ({
    //
  }),
};
</script>
