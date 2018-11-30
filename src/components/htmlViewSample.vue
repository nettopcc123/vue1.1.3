<template>
    <div>
        <div class="iftop">
        <!-- <div class="bghid"></div>     -->
        <iframe ref="iframe" id="bdIframe" :src="bdTokenUrl" frameborder="0" scrolling="auto" width="100%" height="100%" ></iframe>
        </div>
    </div>
</template>

<script>
import $ from 'jquery';
import { setTimeout } from 'timers';
//http://sports.qq.com/kbsweb/kbsshare/gamelist.htm?#nav-laliga
    export default {
        data() {
            return {
                bdTokenUrl: 'https://m.sporttery.cn/app/zf/fb/livelist.html' //https://m.sporttery.cn/app/zf/fb/livelist.html  https://m.sporttery.cn/app/zf/fb/livelist.html http://www.yidianzixun.com/#/?id=c2&name=%E4%BD%93%E8%82%B2
            }
        },
        // created() {
        //     this.getUrl();
        //     this.$nextTick(()=>{
        //         this.getCode();
        //     });
        // },
        mounted(){
            this.$nextTick(() => {//在下次 DOM 更新循环结束之后执行延迟回调
                $('.bghid').on('click',function(){
                    return;
                })
                // setTimeout(function(){
                //     alert('1aaa')
                //     $('#bdIframe').attr('height','100000px');
                //     $('#bdIframe').attr('style','width:100%;height:100000px');
                //     $('.bghid').attr('style','height:100000px');
                // },1000)
            })
            /**
             * iframe-宽高自适应显示   
             */
            const oIframe = document.getElementById('bdIframe');
            const deviceWidth = document.documentElement.clientWidth;
            const deviceHeight = document.documentElement.clientHeight;
            oIframe.style.width =  '100%'; //数字是页面布局宽度差值
            oIframe.style.height = '100%'; //数字是页面布局高度差
        }
    }
</script>

<style lang="scss" scoped>
@import "scss/base.scss";
.child-view{
    height:100%;
}
.iftop{
    height: 100%;
    position: relative
}
.bghid{
    width: 100%;
    height:100%;
    background:rgba(255,255,255,0.01);
    position: absolute;
    left:0px;
    top:0px;
    height: 100%;
}
</style>
