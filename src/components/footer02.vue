<template>
    <div class="footer">
        <ul>
            <li>
                <router-link :to="{ name: 'Index'}">
                    首页
                </router-link>
             </li>
            <li >
                <router-link :to="{ name: 'htmlViewSample'}">
                   赛程
                </router-link>
            </li>
            <li>
                <router-link :to="{ name: 'frameNew'}" v-bind:class="{ active: isNews }">
                   新闻
                </router-link>
            </li>
            <li>
                <router-link :to="{ name: 'disclaimer'}"  v-bind:class="{ active: isActive }">
                   球衣
                </router-link>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
  name: 'App',
  data(){  
        return{  
            isActive: false,
            isNews: false,
        }  
    },
  　watch: {
　　　'$route' (to, from) {
       var isBack = this.$router.isBack; // 监听路由变化时的状态为前进还是后退
　　　　　　if(isBack) {
　　　　　　　this.transitionName = 'slide-right';
　　　　　　} else {
　　　　　　 this.transitionName = 'slide-left';
　　　　　}
　　    this.$router.isBack = false;
　　},
    $route(to,from){
        if(to.path == '/feedback' || to.path == '/disclaimer' || to.path == '/message' || to.path == '/favorites' || to.path == '/fans' || to.path == '/follow'){ //用户中心
            this.isActive = true;
            this.isBanner = false;
        }else{
            this.isActive = false;
            this.isBanner = false;
        }

        if(to.path == '/newsMore' || to.path == '/newsMore1' || to.path == '/newlists1' || to.path == '/newlists2' || to.path == '/newlists3'){ //新闻中心
            this.isNews = true;
            this.isBanner = false;
        }else{
            this.isNews = false;
            this.isBanner = true;
        }
        if(to.path != from.path){ //滚动条置顶
            document.getElementById('vrw').scrollTop = 0;
        }
        
    },
　 }
}
</script>
<style lang="scss" scoped>
@import "scss/base.scss";
.footer{
    position: fixed;
    bottom:-1px;
    left:0px;
    display: block;
    width: 100%;
    border-top:1px solid #dddddd
}
.footer ul{
    width: 100%;
}
.footer ul li{
    float:left;
    width:25%;
}
.footer ul li a{
    text-align: center;
    background: url('img/footbg.png');
    color:#fff;
    height: 0.4rem;
    display: inherit;
    padding-top: 0.01rem;
    font-size: 0.2rem;
    line-height: 0.4rem;
    border-bottom: 3px solid #3c89cb;
}
.footer ul li .router-link-exact-active{
    border-bottom:3px solid #1461a3;
    background: url('img/footbg_h.png');
}

</style>