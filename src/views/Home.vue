<template>
  <div class="home">
    <p>demos from <a href="https://whatwebcando.today/">https://whatwebcando.today/</a></p>

    <loc />
    <photo />
    <photo-easy />
  </div>
</template>

<script>
import Loc from '@/components/Loc.vue';
import Photo from '@/components/Photo.vue';
import PhotoEasy from '@/components/PhotoEasy.vue';

export default {
  name: 'home',
  components: {
    Loc,
    Photo,
    PhotoEasy
  }
}
</script>
