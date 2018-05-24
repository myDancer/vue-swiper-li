<template>
  <div class="swiper-wrap">
    <Swiper :imgs="imgs"/>
  </div>
</template>

<script>
import Swiper from 'vue-swiper-lj'
export default {
  data () {
    return {
      imgs: [
        'http://p1.music.126.net/JBy1FYoB8QoTPj7LGsGcZQ==/109951163312508936.jpg',
        'http://p1.music.126.net/7mfBQD7u1lZR0eiqb8bTAA==/109951163312449573.jpg',
        'http://p1.music.126.net/UO5gvUIk9RZL78u5ZsoIBA==/109951163312707065.jpg'
      ]
    }
  },
  components: {
    Swiper
  }
}
</script>

<style>
.swiper-wrap{
  width: 730px;
  height: 336px;
  margin: 0 auto;
}
</style>
