<template>
  <div>
    <h1>photo</h1>
    <p><video v-bind:srcObject.prop="mediaStream" autoplay style="height: 180px; width: 240px;"></video></p>
    <p><button @click="takePhoto()">Take Photo!</button></p>
    <p><img :src="capturedImgSrc" id="imageTag" width="240" height="180"></p>
  </div>
</template>

<script>
  /**
   * docs:
   * https://whatwebcando.today/photos.html
   * https://developers.google.com/web/updates/2016/12/imagecapture
   * https://googlechrome.github.io/samples/image-capture/grab-frame-take-photo.html
   */
  export default {
    data() {
      return {
        imageCapture: null,
        capturedImgSrc: null,
        mediaStream: null
      }
    },

    created() {
      navigator.mediaDevices.getUserMedia({video: true})
        .then(mediaStream => {
          this.mediaStream = mediaStream;
          const track = mediaStream.getVideoTracks()[0];
          this.imageCapture = new ImageCapture(track);
        })
        .catch(error => console.error('getUserMedia() error:', error));
    },

    methods: {
      takePhoto() {
        this.imageCapture.takePhoto()
          .then(blob => this.capturedImgSrc = URL.createObjectURL(blob))
          .catch(error => console.error('takePhoto() error:', error));
      }
    }
  }
</script>
