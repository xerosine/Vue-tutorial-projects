<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        Click Me!
    </div>
</template>

<script>
    export default {
        props: [ 'delay' ],
        data() {
            return {
                timer: null,
                reactionTimer: null,
                showBlock: false
            }
        },
        mounted() {
            setTimeout(() => {
                this.showBlock = true
                this.timer = setInterval(() => {
                    this.reactionTimer += 10
                }, 10);
            }, this.delay)
        },
        methods: {
            stopTimer() {
                console.log(this.reactionTimer)
                clearInterval(this.timer)
                this.$emit('end', this.reactionTimer)
            }
        }
    }
</script>

<style>
.block {
    width: 100px;
    background-color: #181;
    padding: 80px;
    margin: 50px auto;
    border: transparent;
    border-radius: 30px;
    font-size: larger;
    font-weight: bold;
    color: white;
}

</style>