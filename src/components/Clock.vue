<template>
    <div id="clock-box">
        <h1>{{time}}</h1>
    </div>
</template>

<script>

export default {
    name: 'Clock',
    data() {
      return {
        time: ''
      }
    },
    methods: {
        updateClock: function(){
            let currentTime = new Date();
            let hours = currentTime.getHours();
            let minutes = currentTime.getMinutes();
            let seconds = currentTime.getSeconds();

            if (hours<10) {
                hours = "0"+hours;
            }
            if (minutes<10) {
                minutes = "0"+minutes;
            }
            if (seconds<10) {
                seconds = "0"+seconds;
            }

            let clockTime = hours + ':' + minutes + ':' + seconds;

            this.time = clockTime;
        }
    },
    mounted() {
        this.updateClock();
        const oneSecond = 1000;
        setInterval(this.updateClock,oneSecond,this);
    }
}
</script>


<style scoped>
#clock-box {
    height: calc(100% - 2px);
    border: black 1px solid;
    display: flex;
    background-color: #222;
    justify-content: center;
    align-items: center;
    font-size: 48px;
    color: green;
}
</style>

