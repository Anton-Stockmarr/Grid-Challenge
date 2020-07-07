<template>
    <div :class="{listGame: this.type==='list', gridGame: this.type==='grid'}">
        <img :src="this.source">
        <div class="game-name" v-if="type==='list'">
            <h1>{{name}}</h1>
        </div>
    </div>
</template>



<script>
export default {
    name: 'Game',
    props: ["id","name","image","type"],
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

img {
    height: 65px;
    width: 50px;
}


.listGame {
    background-color: white;
    border: 1px black solid;
    height: 65px;
    padding: 5px 10px;
}

.listGame img {
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

.gridGame {
    background-color: white;
    border: 1px black solid;
    display: flex;
    justify-content: center;
    align-items: center;
    height: calc(100% - 2px);
    width: calc(100% - 2px);
}

</style>