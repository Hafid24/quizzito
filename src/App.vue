<template>
  <div id="app" class="flex flex-row flex-justify-center">
    <div class="flex">
      <div v-if="!showScore" class="flex flex-column align-center" >
        <Indicator :step="next" :maxSteps="data.length"/>
        <Quiz :submit="submit" :question="question" :styles="quizContainerstyles"/>
      </div>
      <div v-else class="flex" v-bind:style="quizContainerstyles">
        {{score}}
      </div>
    </div>
    <div class="flex card" v-bind:style="bookContainerstyles" >
      <div class="flex flex-column ">
        <span class="text-gray mt-1">...أنت تلعب الآن</span>
        <h4 class="mt-1"> الثعلب والأسد</h4>
         <img :src="'../src/assets/lion.jpg'">
      </div>
    </div>
  </div>
</template>

<script>
import Indicator from './components/Indicator.vue'
import Quiz from './components/Quiz.vue'
import Data from './arabicData.json'


export default {
  name: 'app',
  components: {
    Indicator,
    Quiz
  },
  data () {
    return {
      data: [],
      question: {},
      next: 0,
      score: 0,
      showScore: false,
      quizContainerstyles: {
		    'width': '450px'
	    },
      bookContainerstyles: {
         'width': '380px'
      }
    }
  },
 methods:{
    init(){
      this.data = Data;
      this.question = this.data[this.next]
    },
    submit(rightAnswer){
      if(rightAnswer) {
        this.score +=1 ;
      }
      if(this.next < (this.data.length - 1 )) {
        this.next += 1;
        this.question = this.data[this.next];
      } else {
        this.showScore = true;
      }
    }
  },
    mounted(){
    this.init()
    }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px; 
}
.card {
  position: relative;
  margin-left: 1rem;
  padding: 1.25rem;
  margin-top: 0.5rem;
  border-radius: .25rem;
  background-color: #fff;
  background-clip: border-box;
  border: 1px solid rgba(0,0,0,.125);
  transition: all 0.3s ease;
}

.align-center {
  align-items: center;
}
.card:hover {
  margin-top: -5px;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.05);
}
.flex {
  display: flex
}
.flex-column  { 
  flex-direction: column 
}
.flex-row { 
  flex-direction: row 
}
h4 {
  font-family: "Product Sans", "Cairo", Helvetica, Arial, serif;
  line-height: 1.5;
  font-size: 1.5rem;
}
.title {
  padding-bottom: .5rem;
}
.text-gray {
  color: #a7a2ce ;
  padding-bottom: 0.5rem;
}
.mt-1 {
  margin-top: 0.24rem;
}
img {
  vertical-align: middle;
  border-style: none;
  width: 100%;
  vertical-align: middle;
}
</style>
