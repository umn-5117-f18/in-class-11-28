<template>
  <div>
    <h1>photo easy</h1>
    <input type="file" accept="image/*" capture @change="onChange($event.target.files)">
    <p><img :src="imgUrl" id="imageTag" width="240" height="180"></p>
  </div>
</template>

<script>
  /**
   * This is an easy photo/camera widget that works well with mobile devices.
   * 
   * remove the "capture" attr on the input to allow uploads from the camera roll.
   * 
   * docs:
   * https://developers.google.com/web/fundamentals/media/capturing-images/
   * https://developer.mozilla.org/en-US/docs/Web/API/File/Using_files_from_web_applications
   */
  export default {
    data() {
      return {
        imgUrl: null
      }
    },
    methods: {
      onChange(files) {
        this.imgUrl = URL.createObjectURL(files[0]);
      }
    },
  }
</script>
