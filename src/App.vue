<template>
    <div id="app">
        <my-header />
<!--        <star />-->
        <poem />
        <main1 />
        <music />

    </div>
</template>
<script lang="ts">
    import Music from './components/music.vue'
    import Star from './components/star.vue'
    import Poem from './components/poem.vue'
    import Main1 from './components/main.vue'
    import MyHeader from './components/header.vue'
    import {Component, Vue} from "vue-property-decorator";

    @Component({
        components: {Music, Star, MyHeader, Poem, Main1}
    })
    export default class App extends Vue {

    }
</script>
<style lang="less">
    * {
        margin: 0;
        padding: 0;
        font-family: "Noto Sans SC";
        font-weight: 100;
    }

    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        position: relative;
        overflow: hidden;
    }
    h1 {
        font-weight: bold;
    }
    body {
        color: #606975;
    }
</style>
