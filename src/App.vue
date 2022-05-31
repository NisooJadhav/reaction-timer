<template>
  <div>
    <h1>Reaction Timer</h1>
    <p class="appears">click as fast as you can</p>
    <button @click="start" :disabled="isPlaying"> Play </button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
    <Results v-if="showResults" :score="score"/>
  </div>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: { Block,Results, Results },
  data(){
    return{
      isPlaying:false,
      delay:null,
      score:null,
      showResults:false
    }
  },
  methods:{
    start(){
      this.delay=2000 + Math.random()*5000
      this.isPlaying=true
      this.showResults=false
    },
    endGame(reactionTime){
this.score=reactionTime
this.isPlaying=false
this.showResults=true
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
#app h1{
   text-shadow:1px 1px 25px #42b983;
   color:#fff;
   font-size:60px;
}
.appears{
  color:#44444450;
  font-style:italic;
  font-size:22px;
}
button{
  background-color:#42b983;
  color:#fff;
  font-size:18px;
  border-radius:15px;
  border:none;
  padding:10px;
  cursor:pointer;
}
button:hover{
  box-shadow:1px 2px 15px #2f2f2f90;
  border:2px solid #fff;
}
button[disabled]{
  opacity: 0.5;
  cursor:not-allowed;
}
</style>