<template>
    <div class="search">
        <div class="search-top">
            <router-link to="/">
                <i class="fa fa-arrow-left"></i>
            </router-link>
            <div class="search-box">
                <input type="text" placeholder="搜索音乐、歌手、歌词、用户">
            </div>
    
        </div>
        <div class="singer-classify">
            <i class="fa fa-user-o"></i>
            <span>歌手分类</span>
            <i class="fa fa-chevron-right"></i>
    
        </div>
        <div class="hot-search">
            <span class="hot-title">
                热门搜索
            </span>
            <ul class="hot-list">
                <li>陈奕迅</li>
                <li>战狼2</li>
                <li>潘玮柏</li>
                <li>快乐男声</li>
                <li>远走高飞</li>
                <li>凉凉</li>
                <li>陈粒</li>
                <li>周杰伦</li>
                <li>许嵩</li>
                <li>中国有嘻哈</li>
    
            </ul>
    
        </div>
        <footer-div></footer-div>
    </div>
</template>

<script>
import footer from '../../components/Footer/Footer'
export default {
    components: {
        'footer-div': footer
    },
    data() {
        return {

        }
    },
    created() {
        Promise.all([this.$http.get(`http://localhost:3000/search/suggest?keywords=海阔`),
        this.$http.get(`http://localhost:3000/search?keywords=海阔`)
        ]).then((datas) => {
            // console.log(datas[0],datas[1]);

        });
    }
}
</script>

<style lang="">
body {
    background: #f2f4f5;
}

.search-top {
    display: flex;
    justify-content: space-around;
    align-items: flex-start;
    padding: 15px 10px 5px;
    background-color: #d33a31;
}

.search-top a i {
    display: inline-flex;
    color: #fff;
    font-size: 18px
}

.search-box {
    width: 90%;
}

.search-box input {
    position: relative;
    width: 100%;
    border: 0;
    border: 0;
    border-bottom: 1px solid #edb0ad;
    background: none;
    padding-bottom: 2px;
    color: #fff;
    font-size: 16px;
    line-height: 18px;
    outline: none;
}

.search-box input::-webkit-input-placeholder {
    color: #e0756e;
}

.singer-classify {
    display: flex;
    justify-content: center;
    padding: 15px 0;
    border-bottom: 1px solid #c9cbcc;
}

.singer-classify i {

    color: #c9cbcc;
    font-size: 1.5em;
}

.singer-classify span {
    padding: 5px 10px;
    color: #333;
    font-size: 14px;
}

.hot-search {
    margin: 10px;
}

.hot-title {
    display: inline-block;
    margin: 10px 0;
    color: #8b8c8d;
    font-size: 16px;
}

.hot-list li {
    display: inline-block;
    margin: 0 10px 10px 0;
    padding: 5px;
    border: 1px solid #ced0d0;
    color: #303131;
    border-radius: 8px;
}
</style>
