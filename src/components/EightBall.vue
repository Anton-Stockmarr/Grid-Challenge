<template>
    <div id="eight-ball-box">
        <div id="ask-bar">
            <input type="text" placeholder="ask me anything..." v-model="question">
            <button @click="ask()">Ask</button>
        </div>
        <div id="ball-image">
            <img src="@/assets/8-ball (clean).png" alt="">
            <img :class="{phaseOut: emptyBall}" src="@/assets/8-ball.png" alt="">
            <div :class="{phaseOut: !showAnswer}" id="answer">{{pickedAnswer}}</div>
        </div>
        <h1></h1>
    </div>
</template>

<script>

export default {
    name: 'EightBall',
    data() {
      return {
          emptyBall: false,
          showAnswer: true,
          buttonBlocker: false,
          question: '',
          answers: [
            "Try again later",
            "Follow your heart",
            "I really don't care",
            "Maybe...",
            "Try Google"
          ],
          pickedAnswer: ''
      }
    },
    methods: {
        ask() {
            if (this.buttonBlocker){
                return;
            }
            this.buttonBlocker = true;
            this.emptyBall = true;
            this.showAnswer = false;

            let self = this;
            setTimeout(function(){
                if (self.question===''){
                    self.pickedAnswer = "You're wasting my time";
                } else {
                    self.pickedAnswer = self.answers[Math.floor(Math.random() * self.answers.length)];
                }
                self.buttonBlocker = false;
                self.showAnswer = true;
            }, 1000,this);
        }
    }
}
</script>


<style scoped>
#eight-ball-box {
    height: calc(100% - 42px);
    border: black 1px solid;
    background-color: #DFAD98;
    padding: 20px 20px;
}

#ask-bar {
    display: block;
    width: 100%;
    height: 32px;
}

#ask-bar input{
    font-size: 16px;
    display: block;
    float: left;
    padding: 5px 10px;
    width: calc(100% - 24px - 48px - 20px);
    height: calc(100% - 14px);
}

#ask-bar button {
    display: block;
    float: right;
    width: 48px;
    height: 32px;
}

#ball-image {
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    margin: 30px 0;
    height: 300px;
}

#ball-image img{
    position: absolute;
    width: 100%;
    max-width: 300px;
    -webkit-transition: opacity 1s ease-in-out;
    -moz-transition: opacity 1s ease-in-out;
    -o-transition: opacity 1s ease-in-out;
    transition: opacity 1s ease-in-out;
}

.phaseOut{
    opacity: 0;
}

#answer {
    text-align: center;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 20%;
    max-width: 50px;
    -webkit-transition: opacity 1s ease-in-out;
    -moz-transition: opacity 1s ease-in-out;
    -o-transition: opacity 1s ease-in-out;
    transition: opacity 1s ease-in-out;
}

</style>

