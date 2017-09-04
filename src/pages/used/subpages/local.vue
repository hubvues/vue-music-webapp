<template>
  <div>
    <div class="wl-header">
      <div class="wl-header-top">
        <div class="container">
          <div class="wl-location"><router-link to="/"><i class="fa fa-chevron-left fa-fw"></i></router-link>本地歌曲</div>

          <div class="wl-nav">
            <div class="wl-search"><i class="fa fa-search"></i></div>
            <i class="fa fa-list"></i>
          </div>
        </div>
      </div>
      <div class="wl-tabs">
        <ul class="wl-tab-list">
          <li>歌曲</li>
          <li>文件夹</li>
          <li class="active">歌手</li>
          <li>专辑</li>
        </ul>
      </div>
    </div>
    <div class="main">
      <div class="container">
        <ul class="wl-singer">
          <li>
            <div class="wl-singer-info">
              <img src="../../../assets/img/wl-singer1.jpg" alt="">
              <div class="wl-singer-content">
                <p>陈奕迅</p>
                <span>3首</span>
              </div>
            </div>
            <div class="wl-icon-message">
              <img src="../../../assets/img/singer-more.png" alt="">
            </div>
          </li>
          <li>
            <div class="wl-singer-info">
              <img src="../../../assets/img/wl-singer2.jpg" alt="">
              <div class="wl-singer-content">
                <p>苏打绿</p>
                <span>8首</span>
              </div>
            </div>
            <div class="wl-icon-message">
              <img src="../../../assets/img/singer-more.png" alt="">
            </div>
          </li>
          <li>
            <div class="wl-singer-info">
              <img src="../../../assets/img/wl-singer3.jpg" alt="">
              <div class="wl-singer-content">
                <p>王力宏</p>
                <span>15首</span>
              </div>
            </div>
            <div class="wl-icon-message">
              <img src="../../../assets/img/singer-more.png" alt="">
            </div>
          </li>
          <li>
            <div class="wl-singer-info">
              <img src="../../../assets/img/wl-singer4.jpg" alt="">
              <div class="wl-singer-content">
                <p>张震岳</p>
                <span>20首</span>
              </div>
            </div>
            <div class="wl-icon-message">
              <img src="../../../assets/img/singer-more.png" alt="">
            </div>
          </li>
          <li>
            <div class="wl-singer-info">
              <img src="../../../assets/img/wl-singer5.jpg" alt="">
              <div class="wl-singer-content">
                <p>张靓颖</p>
                <span>6首</span>
              </div>
            </div>
            <div class="wl-icon-message">
              <img src="../../../assets/img/singer-more.png" alt="">
            </div>
          </li>
          <li>
            <div class="wl-singer-info">
              <img src="../../../assets/img/wl-singer6.jpg" alt="">
              <div class="wl-singer-content">
                <p>张杰</p>
                <span>5首</span>
              </div>
            </div>
            <div class="wl-icon-message">
              <img src="../../../assets/img/singer-more.png" alt="">
            </div>
          </li>
          <li>
            <div class="wl-singer-info">
              <img src="../../../assets/img/wl-singer7.jpg" alt="">
              <div class="wl-singer-content">
                <p>TF boy</p>
                <span>2首</span>
              </div>
            </div>
            <div class="wl-icon-message">
              <img src="../../../assets/img/singer-more.png" alt="">
            </div>
          </li>

        </ul>
      </div>


    </div>
    <jiao></jiao>
  </div>
</template>

<script>
import jiao from '../../../components/Footer/Footer'
export default {
components: {
    jiao
  },
}
</script>

<style lang="scss" scoped>
 @import '../../../assets/scss/singer.scss';
</style>
