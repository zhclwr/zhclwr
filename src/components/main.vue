<template>
    <div id="main" :style="{width: (isIpad ? 730 : 980) + 'px'}">
        <h2>part 1 军训</h2>
        <p>1.</p>
        <p>军训时的自我介绍：</p>
        <p>&nbsp;“大家好，我叫WR，是...”</p>
        <p>从此这位同学正式走入我的生活</p>
        <p>...</p>
        <br>
        <br>
        <p>2.</p>
        <p>军训结束前</p>
        <p>“WR，能写下你的联系方式吗？”</p>
        <p>“嗯”</p>
        <p>你写下了qq号 <span>10234859**</span>和手机号码 <span>133651596**</span></p>
        <p>还把你的大名也写在了旁边</p>
        <p>...</p>
        <br>
        <br>
        <h2>part 2 开学</h2>
        <p>也许该庆幸军训结束前留下了你的联系方式，军训假期结束便重新分了班级。</p>
        <p>新的班级，离开了刚接触一个星期的同学，也分开了你我。</p>
        <p>...</p>
        <br>
        <br>
        <h2>part 3 双旦晚会</h2>
        <p>...</p>
        <p>...</p>
        <p>...</p>
        <br>
        <br>
        <h2>part 4 打羽毛球</h2>
        <p>...</p>
        <p>...</p>
        <p>...</p>
        <br>
        <br>
        <h2>part 5 第一场雪</h2>
        <p>...</p>
        <p>...</p>
        <p>...</p>
        <br>
        <br>
        <h2>part 6 激情五月晚会</h2>
        <p>...</p>
        <p>...</p>
        <p>...</p>
        <br>
        <br>
        <h2>part 7 一起走过的路</h2>
        <p>...</p>
        <p>...</p>
        <p>...</p>
        <br>
        <br>
        <h2>part 8 夏天，像一个秋天</h2>
        <p>...</p>
        <p>...</p>
        <p>...</p>
        <br>
        <br>
        <h2>part 9 kiss goodbye</h2>
        <p>...</p>
        <p>...</p>
        <p>...</p>
        <br>
        <br>

    </div>
</template>
<script lang="ts">
    import {Component, Vue} from "vue-property-decorator"
    import Star from './star.vue'
    @Component({
        components:  {Star}
    })
    export default class Header extends Vue {
        created() {
            console.log(`        _              _
       | |            | |
  ____ | |__     ___  | | __      __  _ __
 |_  / | '_ \\   / __| | | \\ \\ /\\ / / | '__|
  / /  | | | | | (__  | |  \\ V  V /  | |
 /___| |_| |_|  \\___| |_|   \\_/\\_/   |_|

                                           `)
        }
        get isIpad() {
            return !!(navigator.userAgent.match(/Android/i)
                || navigator.userAgent.match(/webOS/i)
                || navigator.userAgent.match(/iPhone/i)
                || navigator.userAgent.match(/iPad/i)
                || navigator.userAgent.match(/iPod/i)
                || navigator.userAgent.match(/BlackBerry/i)
                || navigator.userAgent.match(/Windows Phone/i));
        }
    }
</script>
<style lang="less" scoped>
    #main {
        width: 870px;
        border-left: 1px solid #f1f1f1;
        border-right: 1px solid #f1f1f1;
        margin: 27px auto;
        min-height: 500px;
        padding: 50px 50px;
        font-family: "Noto Sans SC",serif;
        color: #f1f1f1;
        h2 {
            /*text-align: center;*/
            margin-bottom: 15px;
        }
        p {
            text-indent:2em;
            font-size: 1rem;
            font-family: 'Playball', cursive;
        }
        span {
            color: black;
        }

    }
</style>