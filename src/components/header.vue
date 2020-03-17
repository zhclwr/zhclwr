<template>
    <div class="header">
        <div id="title"></div>
        <star />
        <div id="vertical">
            <h1>夏天，秋天</h1>
            <h2>生活是没有标准答案的。</h2>
        </div>
    </div>
</template>
<script lang="ts">
    import {Component, Vue} from "vue-property-decorator"
    import Star from './star.vue'
    @Component({
        components:  {Star}
    })
    export default class Header extends Vue {
        name = "麋鹿鲁哟"
    }
</script>
<style scoped lang="less">
    .header {
        height: 270px;
        width: 100%;
        z-index: 1;
        text-align: center;
        display: table;
        /*background: url(https://img.xjh.me/random_img.php?type=bg&ctype=nature&return=302) center center / cover no-repeat rgb(34, 34, 34);*/
    }
    #title {
        background: url(https://img.xjh.me/random_img.php?type=bg&ctype=nature&return=302) center center / cover no-repeat rgb(34, 34, 34);
        overflow: hidden;
        width: 100%;
        height: 270px;
        max-height: 300px;
        box-shadow: 0 1px 2px rgba(150, 150, 150, .7);
        text-align: center;
        display: table;
        margin-bottom: 1rem;
        z-index: 1;
    }
    #vertical {
        z-index: 2;
        display: table-cell;
        vertical-align: middle;
        color: #ffffff;
        font-family: 'Playball', cursive;
        h1 {
            font-weight: bold;
            text-align: center;
            font-size: 3em;
        }
        h2 {
            margin: 0;
            font-size: 1rem;
            line-height: 1.5em;
            font-weight: 400;
            letter-spacing: .01rem;
            color: rgba(255, 255, 255, 0.8);
            -webkit-animation: fade-in-down .9s;
            animation: fade-in-down .9s both;
            -webkit-animation-delay: .1s;
            animation-delay: .3s;
            text-shadow: 0 3px 6px rgba(0, 0, 0, 0.5);
            -webkit-box-orient: vertical;
            -webkit-line-clamp: 10;
            overflow: hidden;
            font-family: 'Playball', cursive;
            border: 0;
        }
    }

</style>
