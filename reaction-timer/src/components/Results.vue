<template>
    <div>
        <p>Reaction Time: {{ reactionTime }}ms</p>
        <p class="comment">{{ comment }}</p>
    </div>
</template>

<script>
    export default {
        props: [ 'reactionTime' ],
        data() {
            return {
                comment: null
            }
        },
        mounted() {
            if (this.reactionTime <= 100){
                this.comment = "**Frame Destroyer \uD83D\uDC80**"
            }else if (this.reactionTime <= 200){
                this.comment = "**Lag Slayer!!!**"
            }else if (this.reactionTime <= 300){
                this.comment = "Ninja Fingers!"
            }else if (this.reactionTime <= 400){
                this.comment = "Good reflexes"
            }else if (this.reactionTime <= 700){
                this.comment = "why u lagging?"
            }else {
                this.comment = "Snails could tap faster.."
            }
        }
    }
</script>

<style>
    .comment {
        color: darkgreen;
        font-size: larger;
    }
</style>