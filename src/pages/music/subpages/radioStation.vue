<template>
  <div>
    <template v-if="radio.isShow">
      <banner :banners="radio.banners"></banner>
      <div class="wzx-radio clearfix">
        <div class="radio-choose clearfix">
          <div class="choose-left choose">
            <i class="choose-headphone">
              <img src="../../../assets/img/wzx-headphone.png" alt="">
            </i>
            <h3>电台分类</h3>
          </div>
          <div class="choose-right choose">
            <i class="choose-headphone">
              <img src="../../../assets/img/wzx-people.png" alt="">
            </i>
            <h3>电台排行</h3>
          </div>
        </div>
        <div class="radio-groom">
          <div class="groom-nav">
  
            <span>电台个性推荐</span>
          </div>
          <div class="groom-list">
            <figure class="groom-item" v-for="item,index in radio.recommend">
              <lazy-image :src="item.picUrl"></lazy-image>
              <figcaption>{{item.name}}</figcaption>
            </figure>
          </div>
        </div>
        <div class="radio-groom">
          <div class="groom-nav">
  
            <span>商业财经</span>
          </div>
          <div class="groom-list">
            <figure class="groom-item" v-for="item,index in radio.type1">
              <lazy-image :src="item.picUrl"></lazy-image>
              <figcaption>{{item.name}}</figcaption>
            </figure>
          </div>
        </div>
        <div class="radio-groom">
          <div class="groom-nav">
  
            <span>明星做主播</span>
          </div>
          <div class="groom-list">
            <figure class="groom-item" v-for="item,index in radio.type2">
              <lazy-image :src="item.picUrl"></lazy-image>
              <figcaption>{{item.name}}</figcaption>
            </figure>
          </div>
        </div>
        <div class="radio-groom">
          <div class="groom-nav">
  
            <span>音乐故事</span>
          </div>
          <div class="groom-list">
            <figure class="groom-item" v-for="item,index in radio.type3">
              <lazy-image :src="item.picUrl"></lazy-image>
              <figcaption>{{item.name}}</figcaption>
            </figure>
          </div>
        </div>
        <div class="radio-groom">
          <div class="groom-nav">
  
            <span>情感调频</span>
          </div>
          <div class="groom-list">
            <figure class="groom-item" v-for="item,index in radio.type4">
              <lazy-image :src="item.picUrl"></lazy-image>
              <figcaption>{{item.name}}</figcaption>
            </figure>
          </div>
        </div>
        <div class="radio-groom">
          <div class="groom-nav">
  
            <span>有声书</span>
          </div>
          <div class="groom-list">
            <figure class="groom-item" v-for="item,index in radio.type5">
              <lazy-image :src="item.picUrl"></lazy-image>
              <figcaption>{{item.name}}</figcaption>
            </figure>
          </div>
        </div>
        <div class="radio-groom">
          <div class="groom-nav">
            <span>电台分类</span>
          </div>
          <div class="radio-top" >
            <div class="radio-top-name" v-for="item,index in radio.catelist" v-if="index<6">{{item.name}}</div>
          </div>
        </div>
        <div class="radio-groom">
          <div class="groom-nav">
            <span>更多分类</span>
          </div>
          <div class="radio-top">
            <div class="radio-top-name"  v-for="item,index in radio.catelist" v-if="index>5">{{item.name}}</div>
          </div>
        </div>
      </div>
    </template>
    <loading v-if="!radio.isShow"></loading>
  </div>
</template>

<script>
import banner from '../../../components/banner'
import lazyImage from '../../../components/lazyImage'
import loading from '../../../components/loading'
import { mapActions, mapState } from 'vuex'
export default {

  components: {
    banner,
    'lazy-image': lazyImage,
    loading,
  },
  computed: mapState({
    radio: state => state.music.radio
  }),
  methods: {
    ...mapActions([
      'getRadioApi'
    ])
  },
  created() {
    this.getRadioApi();

  },

}
</script>

<style lang="scss">
@import '../../../assets/scss/scssBypages/radioStation/station.scss';
</style>
