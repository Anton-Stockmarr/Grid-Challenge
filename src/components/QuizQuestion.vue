<template>
<div id="quiz-question">
    <div id="question-text" >{{question.page}}. {{question.question}}</div>
<div id="buttons">
 <input type="radio" id="answer1" value="1" v-model="picked">
  <label for="answer1" :style="this.labelColor[0].style">{{question.answer1}}</label><br>
  <input type="radio" id="answer2" value="2" v-model="picked">
  <label for="answer2" :style="this.labelColor[1].style">{{question.answer2}}</label><br>
  <input type="radio" id="answer3" value="3" v-model="picked">
  <label for="answer3" :style="this.labelColor[2].style">{{question.answer3}}</label><br>
  <input type="radio" id="answer4" value="4" v-model="picked">
  <label for="answer4" :style="this.labelColor[3].style">{{question.answer4}}</label>
</div>
</div>
</template>

<script>
export default {
    name: "QuizQuestion",
    components: {
    },
    props: ["question"],
    data() {
        return {
            picked: "0",
            labelColor: [{style: "color: black;"}, {style: "color: black;"}, {style: "color: black;"}, {style: "color: black;"}]
        }
    },
    methods : {
        colorWrong: function() {
            if (this.picked !=0){
            this.labelColor[this.picked-1].style = "color: red";
            }
        }
    }
}
</script>


<style scoped>

#buttons {
    padding-top: 10px;
}

#buttons input {
    cursor: pointer;
    height: 30px;
    font-size: 24px;
}

#buttons label {
    padding-left: 10px;
}

#question-text {
    grid-area: question;
    font-size: 20px;
    text-align: center;
}

</style>