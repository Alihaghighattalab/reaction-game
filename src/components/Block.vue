<template>
    <div class="box" v-if="showBox" @click="stopTimer">Click me</div>
</template>
<script>
export default {
    name: "Block",
    data() {
        return {
            showBox: false,
            timer: null,
            reactionTime: null
        };
    },
    props: ["delay"],
    mounted() {
        setTimeout(() => {
            this.showBox = true;
            this.startTimer()
        }, this.delay);
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
};
</script>
<style>
.box {
    width: 400px;
    border-radius: 32px;
    background-color: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
    cursor: pointer;
}
</style>
