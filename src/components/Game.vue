<template>
    <div id="game">
        <img :src="this.source">
        <div class="game-name">
            <h1>{{name}}</h1>
        </div>
    </div>
</template>



<script>
export default {
    name: 'Game',
    props: ["id","name","image"],
    data() {
      return {
          source: ""
        }
    },
    mounted() {
        try {      
            this.source = require(`@/assets/games/${this.image}`);
        } catch (err) {
            console.log(err);
            this.source = require("@/assets/games/NotFound.jpg");
        }
    }
}
</script>



<style scoped>

#game {
    background-color: white;
    border: 1px black solid;
    height: 65px;

    padding: 5px 10px;
}

#game img {
    display: block;
    height: 65px;
    width: 50px;
    float: left;
}


.game-name {
    display: flex;
    float: right;
    width: calc(100% - 70px);
    height: 65px;
    font-size: 20px;
    margin: auto 0 auto 20px;
    align-items: center;
}

</style>