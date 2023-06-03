<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        click me
    </div>
</template>

<script>
export default {
    props: ["delay"],
    data() {
        return {
            showBlock : false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted() {
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        },this.delay);
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10);
        },
        stopTimer() {
            clearInterval(this.timer)
            this.$emit("end", this.reactionTime)
        }
    }
}
</script>

<style>
.block {
    width: 400px;
    padding: 100px 0;
    margin: 40px auto;
    background-color: aqua;
    text-align: center;
    color: black;
    border-radius: 20px;
    user-select: none;
    cursor: pointer;
}
</style>