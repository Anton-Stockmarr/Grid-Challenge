<template>
    <div id="quiz-box" class="box">
        <div id="question" v-bind:key="question.page" v-for="question in questions">
            <QuizQuestion :ref="'question'+question.page" v-show="page==question.page" v-bind:question="question"/>
        </div>
        <button v-if="!first" v-on:click="prev" class="nav-btn" id = "prev-question">Prev</button>            
        <button v-if="!last" v-on:click="next" class="nav-btn" id ="next-question">Next</button>
        <button v-on:click="submit" id ="submit-quiz">Submit</button>
    </div>
</template>


<script>
import QuizQuestion from './QuizQuestion'
export default {
    name: 'Quiz',
    components: {
        QuizQuestion
    },
    data() {
        return {
            page: 1,
            first: true,
            last: false,
            questions: [{
                page: 1,
                question: "You're 3rd place right now in a race. What place are you in when you pass the person in 2nd place?",
                answer1: "1st",
                answer2: "2nd",
                answer3: "3rd",
                answer4: "None of the above",
                correct: "2"
            },
            {
                page: 2,
                question: "What is the airspeed velocity of an unladen swallow?",
                answer1: "10 mph",
                answer2: "40 Fahrenheit",
                answer3: "African or european swallow?",
                answer4: "Pass",
                correct: "3"
            },
            {
                page: 3,
                question: "In 1811, nearly a quarter of all the women in Britain had the same name. Which?",
                answer1: "Mary",
                answer2: "Elizabeth",
                answer3: "Anna",
                answer4: "Martha",
                correct: "1"
            },
            {
                page: 4,
                question: "Which of these numbers is not a prime?",
                answer1: "19",
                answer2: "59",
                answer3: "47",
                answer4: "87",
                correct: "4"
            },
            ]
        }
    },
    methods: {
        next: function(){
            this.page++;
            if (this.page===4){
                this.last = true;
            }
            if (this.page===2 ){
                this.first = false;
            }
        },
        prev: function(){
            this.page--;
            if (this.page===3){
                this.last = false;
            }
            if (this.page===1 ){
                this.first = true;
            }
        },
        submit: function(){
            let audio;
            if (this.isCorrect()){
                audio = new Audio(require('../assets/Correct-answer.mp3'));
            } else {
                audio = new Audio(require('../assets/Wrong-answer.mp3'));
            }
                audio.play();
      },
        isCorrect: function(){
            let picked;
            let correct = true;
            for (let i=0; i<4; i++){
                let question = this.questions[i];

                picked = this.$refs["question"+question.page][0].picked;
                if (!(picked === question.correct)){
                    correct = false;
                    this.$refs["question"+question.page][0].colorWrong();
                }
            }  
            return correct;
        }
    }
}
</script>


<style scoped>
#quiz-box {
    height: calc(100% - 42px);
    background-color: #658B6F;
    border: 1px solid black;
    display: grid;
    padding: 20px;
    grid-template-columns: 1fr 1fr;
    grid-template-rows: 1fr 1fr 1fr 1fr 1fr;
    grid-template-areas:
    "question question"
    "question question"
    "question question"
    "prev next"
    "submit submit";
    grid-gap: 20px;
}

#question {
    grid-area: question;
}

#quiz-box .nav-btn {
    margin-top: 20px;
}

#prev-question {
    grid-area: prev;
}
#next-question {
    grid-area: next;
}
#submit-quiz {
    grid-area: submit;
}
</style>