<template>
  <div class="play-box">
    <div class="play-title">
        <router-link to="/"><i class="fa fa-arrow-left"></i></router-link>
        <div class="info">
          <p>{{detail.name}}</p>
          <span>{{detail.singer}}</span>
        </div>
        <div class="share"><i class="fa fa-share-alt"></i></div>
   </div>

   <div class="album">
     <div :class='isPlay? "music-bar active":"music-bar"'>
       <img src="../../assets/img/music-bar.png" alt="">
     </div>
    <div :class='isPlay? "play-img display":"play-img dispause"'>
      <img :src="detail.picUrl" alt="">
    </div>
    
    <div class="option-meun">
      <span class="fa fa-heart-o"></span>
      <span class="fa fa-download"></span>
      <span class="fa fa-commenting-o"></span>
      <span class="fa fa-ellipsis-v"></span>
  </div>
   </div>
   <div class="playbox-contronl">
      
          <div class="rate">
              <span class="now-rate">00:00</span>
              <div class="view-rate">
                  <div class="bar">
                      <div class="zero">
                      </div>
                  </div>
      
              </div>
              <span class="all-rate">00:00</span>
          </div>
      
          <div class="control">
              <span class="fa fa-random"></span>
              <span class="fa fa-step-backward"></span>
               <span class="fa fa-pause-circle-o" v-if="isPlay" @click="play()"></span>
              <span class="fa fa-play-circle-o" v-if="!isPlay" @click="play()"></span>
              <span class="fa fa-step-forward"></span>
              <span class="fa fa-list-ul controls"></span>
          </div>
          <audio ref="audio" :src="url"></audio>   
      </div>
  </div>
</template>

<script>
    import {
        mapMutations,
        mapState
    } from 'vuex';
    export default {

        data() {
            return {
                id: this.$route.params.id,
                isPlay: false,
                url: '',
                times: '',
                allTime: '',
                detail: {
                    name: '',
                    singer: '',
                    picUrl: '',
                    id: ''
                }
            }
        },
        computed: mapState({
            musicId: state => state.music.musicId
        }),
        methods: {
            play() {
                this.isPlay = !this.isPlay;
                let myaudio = this.$refs.audio;

                if (this.isPlay) {
                    myaudio.play();
                } else {
                    myaudio.pause();
                }
            },

            getMusic(id) {
                Promise.all([
                    this.$http.get('http://localhost:3000/music/url?id=' + id),
                    this.$http.get('http://localhost:3000/song/detail?ids=' + id)
                ]).then(data => {
                    if (data[0].data.code === 200 && data[1].data.code) {
                        this.url = data[0].data.data[0].url;
                        this.detail.name = data[1].data.songs[0].name;
                        this.detail.picUrl = data[1].data.songs[0].al.picUrl;
                        this.detail.singer = data[1].data.songs[0].ar[0].name;
                        this.detail.id = id;
                        let audio = this.$refs.audio;
                        // this.totalTime(audio);
                        // this.countTime(audio);

                    }
                })
            },
            // totalTime: function(audio) {
            //     audio.canplay = function() {
            //         let Time = parseInt(audio.duration);
            //         this.allTime = this.judeg(Time);
            //     };
            // },
            // countTime: function(audio) {
            //     audio.timeupdate = function() {
            //         let nowTimes = parseInt(audio.currentTime);
            //         this.times = this.judeg(nowTimes);
            //     };
            // },
            // judeg: function(time) {
            //     let num;
            //     let time1 = parseInt(time / 60);
            //     let time2 = Time % 60;
            //     if (time1 < 10) {
            //         if (time2 < 10) {
            //             num = '0' + time1 + ':0' + time2;
            //         } else {
            //             num = '0' + time1 + ':' + time2;
            //         }
            //     } else {
            //         if (time2 < 10) {
            //             num = time1 + ':0' + time2;
            //         } else {
            //             num = time1 + ':' + time2;
            //         }
            //     }

            //     return num;
            // }
        },

        created() {
            this.getMusic(this.musicId);
        }
    }
</script>

<style lang="scss">
    .play-box {
        padding: 10px 15px 40px;
        background: #e0e0e0;
        width: 100vw;
        height: 100vh;
        .play-title {
            display: flex;
            justify-content: space-between;
            align-self: center;
            padding-bottom: 10px;
            border-bottom: 1px solid #fdfdfb;
            a {
                display: inline-flex;
                align-self: center;
                i {
                    color: #fff;
                    font-size: 20px;
                }
            }
            .info {
                width: 80%;
                p {
                    line-height: 1.5em;
                    color: #fff;
                    font-size: 18px;
                }
                span {
                    color: #7a7f8a;
                    font-size: 14px;
                }
            }
            .share {
                display: flex;
                align-self: center;
                i {
                    color: #fff;
                    font-size: 18px;
                }
            }
        }
        .album {
            position: relative;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            height: 80%;
            overflow: hidden;
            .music-bar {
                position: relative;
                display: inline;
                transition: all 1s ease;
                z-index: 9;
                img {
                    position: absolute;
                    top: -20px;
                    left: 50%;
                    max-width: 160px;
                    max-height: 180px;
                    margin-left: -30px;
                    transform-origin: 0 0;
                }
            }
            .active {
                transform: rotate(-45deg);
                z-index: 100;
            }
            .play-img {
                max-width: 300px;
                max-height: 300px;
                margin: auto;
                border: 8px solid rgba(41, 45, 56, .4);
                border-radius: 100%;
                img {
                    width: 100%;
                    height: 100%;
                    border: 50px solid #101012;
                    border-radius: 100%;
                }
            }
            .display {
                animation: animations 30s linear infinite;
                animation-play-state: running;
            }
            .dispause {
                animation: animations 30s linear infinite;
                animation-play-state: paused;
            }
            @keyframes animations {
                from {
                    transform: rotateZ(0);
                }
                to {
                    transform: rotateZ(360deg);
                }
            }
            .option-meun {
                display: flex;
                flex-direction: row;
                justify-content: space-around;
                span {
                    color: #bdbebf;
                    font-size: 20px;
                }
            }
        }
        .playbox-contronl {
            .rate {
                display: flex;
                justify-content: space-between;
                align-items: center;
                padding-top: 25px;
                padding-bottom: 25px;
                span {
                    font-size: 16px;
                    color: #f9f7f2;
                }
                .view-rate {
                    position: relative;
                    width: 70%;
                    height: 5px;
                    margin: 0 4px;
                    background-color: #66696a;
                    .bar {
                        position: relative;
                        width: 0;
                        height: 100%;
                        background: #ff3838;
                        .zero {
                            position: absolute;
                            top: 2px;
                            left: -2px;
                            height: 12px;
                            width: 12px;
                            background-color: #fff;
                            transform: translateY(-50%);
                            border-radius: 12px;
                        }
                    }
                }
            }
            .control {
                display: flex;
                justify-content: space-between;
                span {
                    font-size: 30px;
                    color: #fff;
                }
            }
        }
    }
</style>