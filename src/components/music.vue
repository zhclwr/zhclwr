<template>
    <div class="music">
        <div class="container">
            <img class="cd" src="../assets/CD.png" alt="">
            <img src="https://dss2.baidu.com/6ONYsjip0QIZ8tyhnq/it/u=2840766590,343360904&fm=179&app=42&f=PNG?w=150&h=150&s=273C77870D72C68E12F5B17A0300C031"
                 alt="" class="pic">
        </div>
        <div class="time">{{time}}</div>
        <div class="control">
            <img src="../assets/back.png" alt="" :class="{disable: backDisable}" class="c">
            <img v-if="!playing" src="../assets/play.png" alt="" class="c" @click="play">
            <img v-else src="../assets/pause.png" alt="" class="c" @click="play">
            <img src="../assets/forward.png" alt="" :class="{disable: forwardDisable}" class="c">
        </div>
        <audio ref="music"  :src="musicSrc"/>
    </div>
</template>
<script lang="ts">
    import {Component, Vue} from "vue-property-decorator";

    @Component
    export default class Music extends Vue{
        musicSrc = "./assets/love_summer.mp3"
        backDisable = true
        forwardDisable = true
        time = ""
        timeInterval: any = null
        playing = false


        reapir(num: number) {
            if (num < 10) return "0" + num
            else return String(num)
        }

        timeInt() {
            const musicAudio = (this.$refs.music as any)
            const currentTime = parseInt(musicAudio.currentTime)
            const duration = musicAudio.duration
            const currentMin = Math.floor(currentTime / 60)
            const currentSec = currentTime % 60
            const totalMin = Math.floor(duration / 60)
            const totalSec = Math.floor(duration % 60)
            this.time =  `${this.reapir(currentMin)}:${this.reapir(currentSec)} / ${this.reapir(totalMin)}:${this.reapir(totalSec)}`
        }
        play() {
            const music = this.$refs.music as any
            if (music.paused) {
                music.play()
            } else {
                music.pause()
            }
        }
        mounted() {
            const _this = this
            this.$nextTick(()=> {
                const music = _this.$refs.music as any
                music.addEventListener("playing", function(){
                    _this.playing = true
                    _this.timeInterval = setInterval(_this.timeInt, 1000)
                })
                music.addEventListener("pause", function(){
                    _this.playing = false
                    clearInterval(_this.timeInterval)
                })
            })
        }
        get top(){
            return window.innerHeight - 200
        }
    }
</script>
<style lang="less">
    * {
        margin: 0;
        padding: 0;
    }
    .music {
        position: fixed;
        left: 0;
        width: 100px;
        bottom: 0;
        height: 100px;
        background: #FFFFFF;
        overflow: hidden;
        transition: all 0.35s ease-in-out;
        .container {
            position: relative;
            width: 100px;
            height: 100px;
            .cd {
                margin-left: 50px;
                top: 0;
                width: 100%;
                height: 100%;
            }
            .pic {
                position: absolute;
                width: 100%;
                height: 100%;
                top: 0;
                left: 0;
            }
        }
        .time {
            height: 25px;
            line-height: 25px;
            width: 150px;
            text-align: center;
        }
        .control {
            margin-top: 5px;
            height: 20px;
            width: 150px;
            display: flex;
            justify-content: space-around;
            .c {
                height: 20px;
                width: 20px;
            }
            .disable {
                cursor: not-allowed;
            }
        }

    }
    .music:hover {
        width: 150px;
        height: 160px;
        transition: all 0.35s ease-in-out;
        left: 0;
    }

</style>
