<template>
 <div class="personal">
        <div class="personal-center">
            <div class="user">
                <div class="user-info">
                    <div class="user-face">
                        <img src="img/t01214064e2e01cbb69.png" alt="">
                    </div>
                    <div class="user-detail">
                        <p>随音乐而动&nbsp;&nbsp;<span>Lv.7</span></p>
                        <span class="sign"><i class="fa fa-database"></i> 签到</span>
                    </div>
                </div>
                <div class="menu-selcetion">
                    <div class="group group-1">
                        <a><i class="fa fa-envelope-o"></i>我的消息</a>
                        <a><i class="fa fa-diamond"></i>会员中心</a>
                        <a><i class="fa fa-cart-plus"></i>商城</a>
                        <a><i class="fa fa-suitcase"></i>在线听歌面流量</a>
                    </div>
                    <div class="group group-2">
                        <a><i class="fa fa-user-o"></i>我的好友</a>
                        <a class="near"><span class="near-man"><i class="fa fa-map-marker"></i>附近的人</span><p><span>网易云音乐熊猫歪唱大赛</span><i class="fa fa-circle"></i></p></a>

                    </div>
                    <div class="group group-3">
                        <a><span class="skin"><i class="fa fa-user-circle"></i>个性换肤</span><span class="classify">官方红</span></a>
                        <a><i class="fa fa-user-md"></i>听歌识曲</a>
                        <a><i class="fa fa-clock-o" ></i>定时停止播放</a>
                        <a><i class="fa fa-clock-o"></i>音乐闹钟</a>
                        <a><i class="fa fa-car"></i>驾驶模式</a>
                        <a><i class="fa fa-cloud"></i>音乐云盘</a>


                    </div>

                </div>
            </div>
            <ul class="menu-bottom">
                <li><i class="fa fa-moon-o"></i>夜间模式</li>
                <li><a><i class="fa fa-cog"></i>设置</a></li>
                <li><i class="fa fa-power-off"></i>退出</li>
            </ul>
        </div>
    </div>
</template>
<script>
    export default{

    }
</script>
<style lang="">
    html,
        body {
            height: 100%;
        }
        
        .personal {
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, .2);
            overflow-y: visible;
        }
        
        .personal-center {
            position: relative;
            width: 86%;
            height: 100%;
            background: #fff;
        }
        
        .personal-center .user {
            overflow-y: auto;
            height: 93vh;
        }
        
        .user-info {
            padding: 35px 10px 20px;
            background: #b6b6b6;
        }
        
        .user-info .user-face {
            width: 65px;
            height: 65px;
        }
        
        .user-face img {
            width: 100%;
            height: 100%;
            border-radius: 100%;
        }
        
        .user-detail {
            display: flex;
            justify-content: space-between;
            padding-top: 20px;
        }
        
        .user-detail p {
            color: #f0f0f0;
            font-size: 15px;
        }
        
        .user-detail p span {
            padding: 0 2px;
            border: 1px solid #f0f0f0;
            color: #f0f0f0;
            font-size: 10px;
            border-radius: 6px;
        }
        
        .user-detail .sign {
            padding: 2px 5px;
            border: 1px solid #f0f0f0;
            color: #f0f0f0;
            border-radius: 6px;
        }
        
        .group {
            padding: 0 10px;
        }
        
        .group-2 {
            border-top: 5px solid #f2f4f5;
            border-bottom: 5px solid #f2f4f5;
        }
        
        .group a {
            display: block;
            padding: 12px 0;
            color: #333;
            font-size: 14px;
        }
        
        .group a i {
            display: inline-block;
            color: #999;
            font-size: 16px;
            width: 15px;
            margin-right: 8px;
        }
        
        .group-2 a.near {
            display: flex;
            justify-content: space-between;
        }
        
        .group-2 a.near .near-man {
            color: #333;
            font-size: 14px;
        }
        
        .group-2 a.near .fa-circle {
            margin-left: 10px;
            color: #de3f3f;
            font-size: 10px;
        }
        
        .group-2 a.near p span {
            display: inline-block;
            width: 150px;
            color: #c9c9c9;
            text-align: right;
            overflow: hidden;
            text-overflow: ellipsis;
            white-space: nowrap;
        }
        
        .group-3 a:first-child {
            display: flex;
            justify-content: space-between;
        }
        
        .group-3 a:first-child .skin {
            color: #333;
            font-size: 14px;
        }
        
        .group-3 a:first-child .classify {
            color: #c9c9c9;
        }
        
        .menu-bottom {
            position: absolute;
            left: 0;
            bottom: 0;
            display: flex;
            justify-content: space-between;
            width: 100%;
            padding: 15px 10px;
            background: #fff;
            border-top: 1px solid #d9d9d9;
        }
        
        .menu-bottom li {
            color: #333;
            font-size: 15px;
        }
        
        .menu-bottom li a {
            color: #333;
            font-size: 15px;
        }
        
        .menu-bottom li i {
            margin-right: 10px;
            ;
        }
</style>
