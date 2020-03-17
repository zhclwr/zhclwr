<template>
    <div class="poem">
        <div class="poem-border poem-left"></div>
        <div class="poem-border poem-right"></div>
        <div class="poem-sentence">一生中可以喜欢很多人，但心疼的只有一个。</div>
        <div class="poem-info">《不知道是谁说的》</div>
    </div>
</template>
<script lang="ts">

    import {Component, Vue} from "vue-property-decorator";

    @Component({
        components: {}
    })
    export default class App extends Vue {

    }
</script>
<style lang="less">
    .poem {
        position: relative;
        width: 730px;
        max-width: 80%;
        border: 2px solid #797979;
        border-top: none;
        text-align: center;
        margin: 10px auto;
        .poem-border {
            position: absolute;
            height: 2px;
            width: 27%;
            background-color: #797979;
        }
        .poem-left {
            left: 0;
        }
        .poem-right {
            right: 0;
        }
        h1 {
            position: relative;
            margin-top: -20px;
            display: inline-block;
            letter-spacing: 4px;
            color: #797979;
            font-size: 2em;
            margin-bottom: 20px;
        }
        .poem-sentence {
            font-size: 25px;
            padding-top: 36px;
            color: #f1f1f1;
        }
        .poem-info {
            font-size: 15px;
            margin: 15px auto;
            color: #f1f1f1;
        }
    }
</style>
