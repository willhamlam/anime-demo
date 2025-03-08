<template>
<div :class="cn('flex flex-col items-center justify-center', containerClass)">
    <canvas
    id="canvas"
    ref="canvasRef"
    class="absolute z-0"
    :style="{ filter: isSafari ? `blur(${blur}px)` : undefined }"
    ></canvas>
    <div :class="cn('relative z-10', customClass)">
    <slot />
    </div>
</div>
</template>

<script>
import { createNoise3D } from "simplex-noise";
import { cn } from "@/lib/utils";

export default {
    name: 'WavyBackground',
    props: {
        customClass: {
            type: String,
            default: ''
        },
        containerClass: {
            type: String,
            default: ''
        },
        colors: {
            type: Array,
            default: () => [
                "#38bdf8", 
                "#818cf8", 
                "#c084fc", 
                "#e879f9", 
                "#22d3ee"
            ]
        },
        waveWidth: {
            type: Number,
            default: 50
        },
        backgroundFill: {
            type: String,
            default: "white"
        },
        blur: {
            type: Number,
            default: 10
        },
        speed: {
            type: String,
            default: "fast",
            validator: (value) => ["slow", "fast"].includes(value)
        },
        waveOpacity: {
            type: Number,
            default: 1
        }
    },
    data() {
        return {
            isSafari: false,
            w: 0,
            h: 0,
            nt: 0,
            ctx: null,
            animationId: null,
            noise: createNoise3D()
        };
    },
    methods: {
        getSpeed() {
            return this.speed === "slow" ? 0.008 : 0.009;
        },
        init() {
            const canvas = this.$refs.canvasRef;
            if (canvas) {
                this.ctx = canvas.getContext("2d");
        if (this.ctx) {
            // 设置固定尺寸 100*100
            const fixedWidth = 100;
            const fixedHeight = 100;
            const pixelRatio = 2;
            
            // 设置显示尺寸
            canvas.style.width = fixedWidth + 'px';
            canvas.style.height = fixedHeight + 'px';
            
            // 设置实际渲染尺寸（乘以 pixelRatio）
            this.w = this.ctx.canvas.width = fixedWidth * pixelRatio;
            this.h = this.ctx.canvas.height = fixedHeight * pixelRatio;
            
            // 缩放上下文以匹配 pixelRatio
            this.ctx.scale(pixelRatio, pixelRatio);

            this.ctx.filter = `blur(${this.blur}px)`;
            
            // 移除窗口大小调整事件，因为我们现在使用固定尺寸
            window.onresize = null;
            
            this.render();
        }
            }
        },
        drawWave(n) {
            this.nt += this.getSpeed();
            for (let i = 0; i < n; i++) {
                this.ctx.beginPath();
                this.ctx.lineWidth = this.waveWidth;
                this.ctx.strokeStyle = this.colors[i % this.colors.length];
                for (let x = 0; x < this.w; x += 5) {
                const y = this.noise(x / 80, 0.4 * i, this.nt) * 4;
                this.ctx.lineTo(x, y + this.h * 0.25); // Adjust for height, at 50% of the container
                }
                this.ctx.stroke();
                this.ctx.closePath();
            }
        },
        render() {
        if (this.ctx) {
            this.ctx.fillStyle = this.backgroundFill;
            this.ctx.globalAlpha = this.waveOpacity;
            this.ctx.fillRect(0, 0, this.w, this.h);
            this.drawWave(5);
            this.animationId = requestAnimationFrame(this.render);
        }
        },
        cn
    },
    mounted() {
        this.isSafari = 
        typeof window !== "undefined" &&
        navigator.userAgent.includes("Safari") &&
        !navigator.userAgent.includes("Chrome");

        this.init();
    },
    beforeUnmount() {
        if (this.animationId) {
        cancelAnimationFrame(this.animationId);
        }
    }
}
</script>