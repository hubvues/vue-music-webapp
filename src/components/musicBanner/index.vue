
<template>
  <div>
    <div class="subnav">
      <ul class="zql-hot">
        <li v-for="item,index in navs" @click="moveActive(index)">
          <a>{{item.text}}</a>
        </li>
        <div class="move" :style="{left:isActive*25+'%'}"></div>
      </ul>
    </div>
    <div class="wzx-banner">
      <swiper :options="swiperOption" :not-next-tick="notNextTick" ref="mySwiper">
        <swiper-slide>
          <recommend></recommend>
        </swiper-slide>
        <swiper-slide>
          <lists></lists>
        </swiper-slide>
        <swiper-slide>
          <songSheet></songSheet>
        </swiper-slide>
        <swiper-slide>
          <radioStation></radioStation>
        </swiper-slide>
      </swiper>
    </div>
  </div>
</template>

<script>
import { swiper, swiperSlide } from 'vue-awesome-swiper'
import recommend from '../../pages/music/subpages/recommendation'
import lists from '../../pages/music/subpages/lists'
import radioStation from '../../pages/music/subpages/radioStation'
import songSheet from '../../pages/music/subpages/songSheet'

export default {
  components: {
    swiper,
    swiperSlide,
    recommend,
    lists,
    radioStation,
    songSheet,

  },
  data() {
    return {
      isActive: 0,
      navs: [{
        text: '热门推荐',
      },
      {
        text: '榜单',
      },
      {
        text: '歌单',
      },
      {
        text: '电台',
      }
      ],
      notNextTick: true,
      swiperOption: {
        grabCursor:true,
        setWrapperSize: true,
        paginationClickable: true,
        mousewheelControl: false,
        observeParents: true,
        loop: true,
        spaceBetween: 30,
        onSlideChangeStart: swiper=> {
          this.isActive = swiper.realIndex;
        }
      
    },
    }

},
computed: {
  swiper(){
    return this.$refs.mySwiper.swiper;
  }
},

methods: {
  moveActive(index) {
    this.isActive = index;
    this.swiper.slideTo(index + 1, 300, false);
    
  }
},
}
</script>

<style lang="scss" scoped>
.subnav {
  position: fixed;
  top: 72px;
  width: 100%;
  z-index: 100;
  background: rgba(255, 255, 255, .9);
  .zql-hot {
    position: relative;
    .move {
      position: absolute;
      bottom: 0;
      left: 0;
      width: 25%;
      height: 4px;
      background-color: #b30000;
      transition: all .5s ease;
    }
  }
}

.wzx-banner {
  margin-top: 122px;
}
</style>
