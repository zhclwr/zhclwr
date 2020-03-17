<template>
    <canvas ref="starCanvas" id="starCanvas" />
</template>
<script lang="ts">
    import {Component, Vue} from "vue-property-decorator"
    import * as THREE from 'three'

    @Component
    export default class Star extends Vue {
        windowWidth = 0
        windowHeight = 0
        renderer:any = null
        scene:any = null
        camera:any = null
        light:any = null
        particles:any = null
        particle:any = null
        mouse = {
            x: 0,
            y: 0
        }
        mounted() {
            this.$nextTick(() => {
                this.windowWidth = 3000
                this.windowHeight = 2000
                this.init();
                // 设置动画开始点
                this.mouseMove({clientX: window.innerWidth / 2, clientY: 140})
            })
        }
        init() {
            this.renderer = new THREE.WebGLRenderer({
                canvas: this.$refs.starCanvas as HTMLCanvasElement
            })
            // this.renderer.setClearColor(0x000000, 0.0);
            this.renderer.setSize(this.windowWidth, this.windowHeight)
            this.scene = new THREE.Scene({ antialias: true })
            this.scene.fog = new THREE.FogExp2(0x1b1b1b, 0.0001);
            this.camera = new THREE.OrthographicCamera(this.windowWidth / -2, this.windowWidth / 2, this.windowHeight / 2, this.windowHeight / -2, 0, 1000)
            this.camera.position.set(0, 0, 500)
            this.scene.add(this.camera)
            this.light = new THREE.DirectionalLight(0xffffff, 1)
            this.light.position.set(0, 250, 700)
            this.scene.add(this.light)
            this.particles = new THREE.Object3D()
            this.scene.add(this.particles)
            document.addEventListener("mousemove", this.mouseMove)
            document.addEventListener("touchemove", this.mouseMove)
            this.renderer.render(this.scene, this.camera)
            this.animate()
        }
        animate() {
                requestAnimationFrame(this.animate)
                this.createParticle()
                for (let i = 0, j = this.particles.children.length; i < j; i++) {
                    let particle = this.particles.children[i]
                    particle.geometry.vertices[0].x += (particle.direction.x - particle.geometry.vertices[0].x) * particle.speed
                    particle.geometry.vertices[0].y += (particle.direction.y - particle.geometry.vertices[0].y) * particle.speed
                    particle.material.opacity -= .008
                    particle.geometry.verticesNeedUpdate = true
                    if (particle.material.opacity < .05) {
                        this.particles.remove(particle)
                        i--
                        j--
                    }
                }
                this.renderer.render(this.scene, this.camera)
        }
        mouseMove(e: any) {
            this.mouse.x = e.clientX - (this.windowWidth / 2)
            this.mouse.y = (this.windowHeight / 2) - e.clientY
        }
        createParticle() {
            let geometry = new THREE.Geometry()
            let  vertices = new THREE.Vector3(
                this.mouse.x,
                this.mouse.y, -10
            )
            geometry.vertices.push(vertices)
            let material = new THREE.PointCloudMaterial({
                color: new THREE.Color(0xffffff),
                size: this.isIpad ? 6 : 3,
                transparent: true,
                opacity: 0.8,
                sizeAttenuation: false
            })
            this.particle = new THREE.PointCloud(geometry, material)
            this.particle.speed = Math.random() / 100 + 0.002
            this.particle.direction = {
                x: (Math.random() - .5) * this.windowWidth * 3,
                y: (Math.random() - .5) * this.windowHeight * 2
            }
            this.particles.add(this.particle)
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
<style scoped>
    #starCanvas {
        position: fixed;
        top: 0;
        width: 100%;
        height: 270px;
        z-index: -1;
    }
</style>