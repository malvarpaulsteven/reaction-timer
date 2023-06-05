<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        Click Me!
    </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0,
            ms: null
        }
    },
    mounted() {
        setTimeout(() => (
            this.showBlock = true,
            this.startTimer()
        ), this.delay)
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10,
                this.ms = "milliseconds"
            }, 10)
        },
        stopTimer() {
            clearInterval(this.timer),
            this.$emit('end', this.reactionTime),
            this.$emit('ms', this.ms)
        }
    }
}
</script>

<style>
    .block {
        width: 400px;
        border-radius: 20px;
        background: #0faf87;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>