<template>
  <div>
    <h1>location</h1>
    <pre>{{ lat }}:{{ long }}</pre>

    <iframe 
      v-if="ready"
      width="300" 
      height="170" 
      frameborder="0" 
      scrolling="no" 
      marginheight="0" 
      marginwidth="0" 
      v-bind:src="embedMapUrl"
    >
    </iframe>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        ready: false,
        lat: null,
        long: null
      }
    },

    computed: {
      embedMapUrl() {
        return `https://maps.google.com/maps?q=${this.lat},${this.long}&hl=es;z=14&output=embed`;
      }
    },

    created() {
      navigator.geolocation.getCurrentPosition(this.updateLoc);
      // navigator.geolocation.watchPosition(this.updateLoc);
    },

    methods: {
      updateLoc(loc) {
        this.ready = true;
        this.lat = loc.coords.latitude;
        this.long = loc.coords.longitude;
      }
    },
  }
</script>

<style scoped>

</style>