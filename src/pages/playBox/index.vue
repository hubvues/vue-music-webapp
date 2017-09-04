<template>
    <div class="play-box">
        <div class="play-title">
            <router-link to="/">
                <i class="fa fa-arrow-left"></i>
            </router-link>
            <div class="info">
                <p>{{detail.name}}</p>
                <span>{{detail.singer}}</span>
            </div>
            <div class="share">
                <i class="fa fa-share-alt"></i>
            </div>
        </div>
    
        <div class="album">
            <div :class='isPlay? "music-bar":"music-bar  active"'>
                <img src="../../assets/img/music-bar.png" alt="">
            </div>
            <div :class='isPlay? "play-img display":"play-img dispause"'>
                <div class="imgbox">
                    <img v-if="detail.picUrl===''" src="../../assets/img/play-bg.png" atl="">
                    <img v-if="detail.picUrl!==''" v-bind:src="detail.picUrl" alt="">
                </div>
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
                <span class="now-rate">{{times=times||'00:00'}}</span>
                <div class="view-rate">
                    <div class="bar" v-bind:style="{width:num}">
                        <div class="zero">
                        </div>
                    </div>
                </div>
                <span class="all-rate">{{allTime=allTime||'00:00'}}</span>
            </div>
    
            <div class="control">
                <span class="fa fa-random"></span>
                <span class="fa fa-step-backward"></span>
                <span class="fa fa-pause-circle-o" v-if="isPlay" @click="play()"></span>
                <span class="fa fa-play-circle-o" v-if="!isPlay" @click="play()"></span>
                <span class="fa fa-step-forward"></span>
                <span class="fa fa-list-ul controls"></span>
            </div>
            <audio ref="audio" :src="url" volume='50'></audio>
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
            num: '',
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
                let stopPlay = setInterval(() => {
                    this.contActive(myaudio);
                }, 1000);
                if (this.times === this.allTime) {
                    clearInterval(stopPlay());
                }
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
                    let getAll = setInterval(() => {
                        let Time = parseInt(audio.duration);
                        this.allTime = this.judeg(Time);
                    }, 1000)
                    if (this.allTime === 'number') {
                        clearInterval(getAll);
                    }

                }
            })
        },

        judeg(time) {
            let num;
            let time1 = parseInt(time / 60);
            let time2 = time % 60;
            if (time1 < 10) {
                if (time2 < 10) {
                    num = '0' + time1 + ':0' + time2;
                } else {
                    num = '0' + time1 + ':' + time2;
                }
            } else {
                if (time2 < 10) {
                    num = time1 + ':0' + time2;
                } else {
                    num = time1 + ':' + time2;
                }
            }

            return num;
        },
        contActive(audio) {
            let Time = parseInt(audio.duration)
            let nowTimes = parseInt(audio.currentTime);
            this.times = this.judeg(nowTimes);
            if (this.times === this.allTime) {
                this.isPlay = false;
            }
            this.num = (nowTimes / Time) * 100 + '%';
          
        }

    },

    created() {
        this.getMusic(this.musicId);
    }
}
</script>

<style lang="scss">
@import '../../assets/scss/playbox.scss';
</style>