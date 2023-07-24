<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        click me
    </div>
</template>
<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTimer: 0
        }
    },
    mounted() { // mount hook // on load the component
        console.log(`component mounted`)
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
            console.log(`delay: ${this.delay}`)
        }, this.delay);
    },
    updated() { // updated hook // on update the component
        console.log(`component updated`)
    },
    unmounted() { // unmounted hook // on kill the component
        console.log(`component unmounted`)
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTimer += 10
            }, 10);
        },
        stopTimer() {
            clearInterval(this.timer)
            console.log(`reactionTimer: ${this.reactionTimer}`)
            this.$emit('end', this.reactionTimer)
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