<template>
  <section class="d-flex flex-column align-center">
    <h1 class="mb-5">Camera</h1>
    <v-btn @click="takePicture" color="primary">open camera</v-btn>
    <video ref="video" class="mt-5" autoplay controls></video>
  </section>
</template>

<script>
export default {
  name: 'camera',
  data() {
    return {
      srcObject: false
    };
  },
  methods: {
    takePicture() {
      navigator.mediaDevices
        .getUserMedia({ video: true })
        .then(mediaStream => {
          this.srcObject = true;
          this.$refs.video.srcObject = mediaStream;
        })
        .catch(e => {
          alert(e);
        });
    }
  }
};
</script>

<style lang="scss" scoped>
video {
  max-width: 100%;
}
</style>
