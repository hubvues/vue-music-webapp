<template>
  <div>
    <header-div></header-div>
    <musicBanner></musicBanner>
    <footer-div></footer-div>
  </div>
</template>

<script>
import header from '../../components/Header/Header'
import footer from '../../components/Footer/Footer'
import musicBanner from '../../components/musicBanner/index'
import { swiper, swiperSlide } from 'vue-awesome-swiper'
export default {
  components: {
    'header-div':header,
    'footer-div':footer,
    musicBanner
  },
      data() {
      return {
      }
    }
  
}
</script>

<style lang="scss">
 
</style>
