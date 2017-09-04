<template>
  <div>
    <app-header></app-header>
    <div class="main ">
      <div class="wl-dynamic">
  
        <div class="container">
          <div class="wl-hot-topic">
            <div class="titles">
              <h2>热门话题</h2>
            </div>
            <div class="wl-topic">
              <figure>
                <figcaption class="mark">#你单曲循环最多的是哪一首歌呢？</figcaption>
                <a href="#">
                  <img src="../../assets/img/wl-dynamic1.jpg" alt="">
                </a>
              </figure>
              <figure>
                <figcaption class="mark">#你单曲循环最多的是哪一首歌呢？</figcaption>
                <a href="#">
                  <img src="../../assets/img/wl-dynamic3.jpg" alt="">
                </a>
              </figure>
            </div>
            <ul class="wl-topic-list">
              <li>
                <div class="title">
                  <figure>
                    <img src="../../assets/img/wl-dynamic-user.png" alt="">
                    <div class="wl-content">
                      <figcaption>欢乐颂音乐带你发现世界</figcaption>
                      <span>11-29</span>
                    </div>
                  </figure>
                  <div class="fous">
                    <span>
                      <i>+</i> 关注</span>
                  </div>
                </div>
                <div class="main-info">
                  <article>
                    <p>今天是钟汉良欧巴的生日！想不起来是什么时候开始关注他的作品， 不例外的从电视剧电影里认识他，从而了解原来他还是歌手，并且 获得不少奖项!
                    </p>
                  </article>
                  <div class="medium">
                    <div class="play-video">
                      <video src="" class="moive"></video>
                      <span class="play-times">
                        <i class="fa fa-video-camera"></i>40万</span>
                      <span class="all-time">00:00</span>
                    </div>
                    <div class="img-clums">
                     
                     
                    </div>
                    <div class="audio-box">
                      <audio></audio>
                      <div class="audio-info">
                        <div class="info-face">
                          <img src="" alt="">
                          <i class="fa fa-play-circle-o"></i>
                        </div>
                        <div class="content">
                          <p>We Can't Stop</p>
                          <span>Milley Cytus</span>
                        </div>
                      </div>
  
                    </div>
                    <div class="tag">———最赞粉丝作品</div>
                    <div class="button">
                      <span class="fa fa-thumbs-o-up">
                        <i>10</i>
                      </span>
                      <span class="fa fa-commenting-o">
                        <i>5</i>
                      </span>
                      <span class="fa fa-share-alt">
                        <i>2</i>
                      </span>
                      <span class="fa fa-ellipsis-v"></span>
                    </div>
  
                  </div>
                </div>
              </li>
            </ul>
  
          </div>
        </div>
      </div>
    </div>
    <app-footer></app-footer>
  </div>
</template>

<script>

import header from '../../components/Header/Header'
import footer from '../../components/Footer/Footer'
export default {
  components: {
    'app-header': header,
    'app-footer': footer
  },
  data(){
    return{

    }
  },
  created(){
    Promise.all([this.$http.get(`http://localhost:3000/event`)]).then((datas)=>{
    });
  }
}
</script>
<style lang='scss' scoped>
@import '../../assets/scss/dynamic.scss';
</style>

