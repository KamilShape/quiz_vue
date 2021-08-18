<template>
  <div id="app">
    <MainSection/>
    <h3>Points: {{points}}</h3>
    <Question
    @add='adding($event)'
    v-for='question in questions'
    :key='question.question'
    :question='question.question'
    :answer1='question.answer1'
    :answer2='question.answer2'
    :answer3='question.answer3'
    :answer4='question.answer4'
    :correctAnswer='question.correctAnswer'
    />
      <div class='resultDiv' :class='{display: display}'>The End! Your result is {{points}}</div>
  </div>
</template>

<script>
import MainSection from './components/MainSection.vue'
import Question from './components/Question.vue'
import questions from './assets/data.js'

export default {
  data(){
    return{
      questions,
      answers: [],
      goodAnswers: [],
      display: false,
    }
  },
  name: 'App',
  components: {
    MainSection,
    Question
  },
  methods:{
    adding(item){
      if(item.length === 2){
        this.goodAnswers.push(item[0])
        this.answers.push(item[1])
        console.log(this.questions.length)
        if(this.answers.length == questions.length){
          this.display = true
        }
      } else {
        this.answers.push(item[0])
        if(this.answers.length == questions.length){
          this.display = true
        }
      }
    
    },
  },
  computed:{
    points: function(){
      return this.goodAnswers.length 
    }
    }   
  }  

</script>

<style>
*{
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 30px;
}
.resultDiv{
  display: none;
  font-size: 50px;
  position: fixed;
  z-index: 2;
  left: 50%;
  top: 50%;
  transform: translate(-50%,-50%);
  background-color: lightyellow;
  padding: 35px;
  border-radius: 50px;;
}
.display{
  display: block;
}
</style>
