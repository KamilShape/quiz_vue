<template>
  <div class="hello">
    <h3 class='question'>{{question}}</h3>
    <section class='divSection'> 
      <button class='answer' :disabled='disabled' @click='clickedButton(answer1, question)'>{{answer1}}</button>
      <button class='answer' :disabled='disabled' @click='clickedButton(answer2, question)'>{{answer2}}</button>
      <button class='answer' :disabled='disabled' @click='clickedButton(answer3, question)'>{{answer3}}</button>
      <button class='answer' :disabled='disabled' @click='clickedButton(answer4, question)'>{{answer4}}</button>
    </section>
  
  </div>
</template>
<script>
export default {
  props:{
    question: String,
    answer1: String,
    answer2: String,
    answer3: String,
    answer4: String,
    correctAnswer: String,
  },
  data(){
    return{
      disabled: false,
    }
  },
  methods:{
    clickedButton(answer, question){
      if(answer === this.correctAnswer){
        this.$emit('add', [answer, question])
        this.disabled = true
      }
      else{
        this.$emit('add', [question])
         this.disabled = true
      }
    }
  }
}
</script>
<style>
.divSection{
  margin: 0 auto;
  display: flex;
  justify-content: space-evenly;
  width: 40%;
  flex-wrap: wrap;
}
.question{
  margin: 0 auto;
  width: 45%;
  font-size: 30px;
  padding: 15px;
}
.answer{
  width: 40%;
  background-color: lightgreen;
  outline:none;
  padding: 5px;
  margin: 3px;
  border-radius: 20px;
}
.answer:hover{
  cursor: pointer;
  background-color: #fff;
}
</style>
