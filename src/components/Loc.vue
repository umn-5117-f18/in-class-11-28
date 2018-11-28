<template>
  <div>
    <h1>location</h1>
    <button @click="getLoc()">get location</button>
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
  /**
   * Geolocation demo.
   * 
   * Doesn't seem to work on mobile using `created` -- have to explicitly ask for permission.
   * 
   * docs:
   * https://whatwebcando.today/geolocation.html
   */
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
      // navigator.geolocation.getCurrentPosition(this.updateLoc);
      // navigator.geolocation.watchPosition(this.updateLoc);
    },

    methods: {
      getLoc() {
        navigator.geolocation.getCurrentPosition(this.updateLoc);
      },

      updateLoc(loc) {
        this.ready = true;
        this.lat = loc.coords.latitude;
        this.long = loc.coords.longitude;
      }
    },
  }
</script>
