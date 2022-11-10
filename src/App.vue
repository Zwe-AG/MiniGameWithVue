<template>
  <h1>How can you catch me fast?</h1>
  <button @click="start" :disabled="isPlaying" :class="{success:isPlaying===false,danger:isPlaying===true}">Play</button>
  <div v-if="isPlaying">
    <Block :delay="delay" @endGame="endGame" />
  </div>
  <div v-if="end">
    <Result :score="score" />
  </div>
</template>

<script>


import Result from './components/Result'
import Block from './components/Block'
export default {
  name: 'App',
  components: {
    Result,
    Block,
    
  },
  data() {
    return {
      isPlaying : false,
      delay : null,
      score: 0,
      end:false
    }
  },
  methods: {
    start(){
      this.isPlaying = true;
      this.end = false;
      this.delay = 2000+Math.random()*5000;
    },
    endGame(score){
      this.score=score;
      this.isPlaying = false;
      this.end = true;
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button{
  font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  font-size: 15px;
  letter-spacing: 2px;
  color:#fff;
  background-color: darkcyan;
  padding: 10px 20px;
  border: none;
  border-radius: 5%;
}
.success{
   color:#fff;
  background-color: darkcyan;
}
.danger{
   color:#fff;
  background-color: crimson;
}
</style>
