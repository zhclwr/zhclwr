<template>
    <div id="app">
        <div id="nav">

        </div>
        <music></music>
    </div>
</template>
<script lang="ts">
    import Music from './components/music.vue'
    import {Component, Vue} from "vue-property-decorator";

    @Component({
        components: {Music}
    })
    export default class App extends Vue{

    }
</script>
<style lang="less">
    * {
        margin: 0;
        padding: 0;
    }
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
    }

    #nav {
        padding: 30px;

        a {
            font-weight: bold;
            color: #2c3e50;

            &.router-link-exact-active {
                color: #42b983;
            }
        }
    }
</style>
