<template>
  <div class="flex flex-column" v-bind:style="styles">
    <div class="question flex flex-justify-center" >
      {{question.question}}
    </div>
    <div id="1"  v-on:click="select($event)" class="answer" v-bind:style="[submiting ? {'cursor': 'none'} : {}]" v-bind:class="{ 'correct-answer ' : !isWrongAnswer(0)  && submiting && answerChecked == 0 , 'wrong-answer' :  isWrongAnswer(0) && submiting && answerChecked == 0 , 'selected' : isSelected(0) && !submiting}">
      {{question.choice1}}
    </div>
    <div id="2"  v-on:click="select($event)" class="answer" v-bind:style="[submiting ? {'cursor': 'none'} : {}]" v-bind:class="{ 'correct-answer ' : !isWrongAnswer(1) && submiting && answerChecked == 1 , 'wrong-answer' :  isWrongAnswer(1) && submiting && answerChecked == 1 , 'selected' : isSelected(1) && !submiting} ">
      {{question.choice2}}
    </div>
    <div id="3"  v-on:click="select($event)" class="answer" v-bind:style="[submiting ? {'cursor': 'none'} : {}]"  v-bind:class="{ 'correct-answer ' : !isWrongAnswer(2)  && submiting && answerChecked == 2 , 'wrong-answer' :  isWrongAnswer(2) && submiting && answerChecked == 2 , 'selected' : isSelected(2) && !submiting}">
      {{question.choice3}}
    </div>
    <div class="submit-btn" v-bind:style="[submiting ? {'cursor': 'none'} : {}]" v-on:click="checkAnswer">
         موافق
    </div>      
    </div>
</template>

<script>
export default {
  name: 'Quiz',
  data () {
    return {
      selections: [false, false, false],
      rightAnswer: false,
      answerChecked: -1,
      submiting: false,
    }
  },
  props: ['question', 'submit', 'styles'],
  watch: { 
    question: function(newVal, oldVal) { 
      if(newVal != oldVal){
        this.selections = [false, false, false];
        this.rightAnswer = false;
        this.answerChecked = -1;
        this.submiting = false;
      };
    },
  },
  methods:{
    checkAnswer(){
      if(this.answerChecked != -1) {
        this.submiting = true;
        setTimeout(() =>{ this.submit( this.rightAnswer); }, 500);
      }
    },
    select(event){
      const targetId = event.currentTarget.id;
      this.selections = this.selections.map((option,index) => (index + 1) == targetId ? (() => { this.answerChecked = index; return !option; })() : false);
      this.rightAnswer = this.question.answer == targetId?  targetId : false;
    },
    isWrongAnswer(id) {
      if(this.answerChecked == id && this.rightAnswer == id ) return true;
      return false;
    },
    isSelected(id) {
        return this.selections[id];
    }
  },
}
</script>

<style>
.question {
  text-align: center;
  margin-bottom: 0.5rem;
  padding-top: 1rem;
  padding-bottom: 0.5rem;
  font-family: "Product Sans", "Cairo", Helvetica, Arial, serif;
  line-height: 1.5;
  font-size: 1.5rem;
}
.answer {
  display: flex;
  margin-bottom: 0.5rem;
  width: 100%;
  font-size: 1.2rem;
  border: 0.1rem solid rgb(86, 165, 235, 0.25);
  background-color: white;
  border-radius: 1rem;
  justify-content: center;
  padding-bottom: 10px;
  padding-top: 10px;
}
.answer:hover:not(.selected) {
  cursor: pointer;
  transform: translateY(-0.1rem);
  transition: transform 150ms;
  background-color: rgba(0,0,0,.15);
}
.selected {
  background-color: orange ;
  color: #fff;
}
.wrong-answer {
  background-color: red !important;
  color: #fff !important;
}
.correct-answer {
  background-color: green !important;
  color: #fff !important;
}
.flex-justify-center { 
  justify-content: center 
}
.submit-btn {
  display: flex;
  font-size: 16px;
  font-family: "Product Sans", "Cairo", Helvetica, Arial, serif;
  line-height: 1.5;
  color: #fff;
  letter-spacing: 2px;
  padding: 17px 35px;
  border-radius: 30px;
  border-color: #28a745;
  background-color: #28a745;
  font-weight: 400;
  align-self: center;
  white-space: nowrap;
  vertical-align: middle;
}
.submit-btn:hover {
  cursor: pointer;
  color: #fff;
  background-color: #218838;
  border-color: #1e7e34;
  transform: translateY(-2px);
  transition: all 0.3s ease;
}
</style>
