<!--
    author:hubvues
-->
<template>
  <div class="wl-lists-rank">
  
    <div class="wl-detail">
      <div class="wl-meun">
        <router-link to="/music/lists">
          <div class="go-back">
            <i class="fa fa-arrow-left"></i>
            <span>{{idxUser.listName}}</span>
          </div>
        </router-link>
        <div class="control">
          <i class="fa fa-search"></i>
          <i class="fa fa-ellipsis-v"></i>
        </div>
      </div>
    </div>
    <div class="wl-detail-banner">
      <div class="banner-info">
        <span class="tags">云音乐</span>
        <img :src='idxUser.picUrl' alt="">
        <i class="fa fa-info-circle  description" @click="isShowInfo=!isShowInfo">
          <p v-if="isShowInfo">{{description}}
            <i class="fa fa-caret-up fa-3x"></i>
          </p>
        </i>
        <span class="up-time">最近更新：7月3日</span>
  
      </div>
      <ul class="control-button">
        <li>
          <i class="fa fa-folder-o"></i>
          <span>{{idxUser.subscribedCount}}万</span>
        </li>
        <li>
          <i class="fa fa-commenting-o"></i>
          <span>{{idxUser.commentCount}}</span>
        </li>
        <li>
          <i class="fa fa-share-alt"></i>
          <span>{{idxUser.shareCount}}</span>
        </li>
        <li>
          <i class="fa fa-download"></i>
          <span>下载</span>
        </li>
      </ul>
    </div>
    <ul class="wl-play-list">
      <div class="title">
        <div class="title-left">
          <i class="fa fa-play-circle-o"></i>
        </div>
        <div class="title-right">
  
          <p>播放全部
            <span>（共{{idx.length}}首）</span>
          </p>
          <span>
            <i class="fa fa-list-ul"></i> 多选</span>
  
        </div>
      </div>
  
      <ul class="rank">
        <li v-for="item,index in idx" @click="changeMusicId(item.id)">
          <div class="rank-left">
            <div class="ranking">
              <i class="fa"></i>
              <span :class="index+1<4? 'active':''">{{index+1}}</span>
              <!-- <p>
                   <i class="fa fa-arrow-up"></i>{{item.score}}%</p>  -->
            </div>
  
          </div>
          <div class="rank-right">
            <div class="songs-name">
              <p class="textLine">
                <span>{{item.name}}</span>{{item.alia[0]}}
              </p>
              <div class="singer-info textLine">
                <span class="hot">SQ</span> {{item.ar[0].name}} - {{item.al.name}}
  
              </div>
            </div>
            <i class="fa fa-ellipsis-v"></i>
          </div>
        </li>
      </ul>
    </ul>
    <loading v-if="!isShow"></loading>
    <playbox></playbox>
  </div>
</template>
<script>
import loading from '../../../components/loading';
import playbox from '../../../components/Footer/Footer';
import { mapMutations } from 'vuex'
export default {
  components: {
    loading,
    playbox,

  },
  data() {
    return {
      isShowInfo: false,
      id: this.$route.params.id,
      idx: [],
      isShow: false,
      description: '',
      idxUser: {
        abulmName: '',
        listName: '',
        picUrl: '',
        shareCount: '',
        subscribedCount: '',
        commentCount: ''
      }

    }
  },
  created() {
    this.$http.get('http://localhost:3000/playlist/detail?id=' + this.id)
      .then(datas => {


        this.description = datas.data.playlist.description;
        this.idxUser.listName = datas.data.playlist.name;
        this.idxUser.picUrl = datas.data.playlist.coverImgUrl;
        this.idxUser.shareCount = datas.data.playlist.shareCount;
        // console.log(this.idxUser.shareCount)
        this.idxUser.subscribedCount = datas.data.playlist.subscribedCount;
        this.idxUser.commentCount = datas.data.playlist.commentCount;
        this.idxUser.subscribedCount = Math.floor(this.idxUser.subscribedCount / 10000);
        this.idx = datas.data.playlist.tracks;
        this.isShow = true;
      })

  },
  methods: {
    ...mapMutations([
      'changeMusicId'
    ])
  }
}
</script>
<style lang="scss">
@import '../../../assets/scss/scssBypages/lists/listsDate.scss';
</style>
