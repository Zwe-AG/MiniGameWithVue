<template>
   <div class="block" v-if="showBlock" @click="stopTimer">Click here {{ delay }}</div>
</template>

<script>
export default {
props:['delay'],
data() {
    return {
        showBlock : false,
        timer : null,
        score : 0
    }
},
mounted() {
    setTimeout(() => {
        this.showBlock = true;
        this.startTimer();
    }, this.delay);
},
methods: {
   startTimer(){
     this.timer = setInterval(() => {
        this.score += 50;
     }, 50);
   },
   stopTimer(){
     clearInterval(this.timer);
     this.$emit('endGame',this.score);
   }
},
}
</script>

<style>
.block{
        background-color: aqua;
        width: 400px;
        height: 300px;
        margin:20px auto;
        padding-top: 30px;
    }
</style>