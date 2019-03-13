<template>
    <section>
        <ul class="left-nav">
            <router-link tag="li" to="/checkout"><i class="iconfont icon-goumai"></i><p>收银</p></router-link>
            <router-link tag="li" to="/store"><i class="iconfont icon-dianpu"></i><p>商城</p></router-link>
            <router-link tag="li" to="/commodity"><i class="iconfont icon-hanbao"></i><p>商品</p></router-link>
            <router-link tag="li" to="/member"><i class="iconfont icon-huiyuanqia"></i><p>会员</p></router-link>
            <router-link tag="li" to="/statistics"><i class="iconfont icon-zuanshi"></i><p>统计</p></router-link>
            <router-link tag="li" to="/set"><i class="iconfont icon-gongnengjianyi"></i><p>设置</p></router-link>
        </ul>
    </section>
</template>
<script>
export default {
    
}
</script>
<style lang="scss">
.left-nav{
    position: fixed;
    left: 0px;
    height: 100%;
    width: 60px;
    background-color: #409EFF;
    text-align: center;
    color: #fff;
    li{
        padding: 10px;
        border-bottom: 1px solid rgba(255, 255, 255, .3);
        p{
            font-size: 12px;
        }
    }
    .iconfont{
        font-size: 24px;
    }
}
</style>

