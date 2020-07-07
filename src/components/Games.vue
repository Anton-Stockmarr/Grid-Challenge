<template>
    <div id="search-results" :class="{shadowBox: type==='list'}">
        <div :class="{gameGrid: type==='grid'}">
            <div :class="{shadowBox: type==='grid'}" v-bind:key="game.id" v-for="game in games" v-show="inSearch(game.name)">
                <Game v-bind="game" v-bind:type="type"/>
            </div>
        </div>
    </div>
</template>

<script>
import Game from './Game'

export default {
    name: 'Games',
    components: {
        Game,
    },
    props: ["searchKey","type"],
    data() {
      return {
          games: [{
                id: 1,
                name: "Heroes of Might and Magic III",
                image: "Homm.jpg"
            },{
                id: 2,
                name: "Fortnite",
                image: "Nope"
            },{   id: 3,
                name: "League of Legends",
                image: "Lol.png"
            },{   id: 4,
                name: "The Last of Us",
                image: "Tlou.jpeg"
            },{   id: 5,
                name: "Age of Empires",
                image: "AoE.png"
            },{   id: 6,
                name: "The Battle for Middle-Earth",
                image: "BfME.png"
            },{   id: 7,
                name: "Sid Meier's Civilization IV",
                image: "Civ6.png"
            },{   id: 8,
                name: "World of Warcraft",
                image: "WoW.png"
            },{   id: 9,
                name: "Tetris",
                image: "Tetris.jpg"
            }]
        }
    },
    methods: {
        inSearch(name) {
            if (name.toLowerCase().includes(this.searchKey.toLowerCase())){
                return true;
            } else {
                return false;
            }
        }
    },
    mounted() {
        this.games.sort(function(a,b) {
                return a.name < b.name ? -1 : a.name > b.name ? 1 : 0; 
            })
    }
}
</script>


<style scoped>

#search-results {
    max-height: 300px;
    overflow: auto;
}

.shadowBox {
    box-shadow: 0 0 7px black;    
}

.gameGrid {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-auto-rows: 1fr;
    grid-gap: 10px 20px;
    padding: 10px 5px;
}

.gameGrid div {
    height: 85px;
}

</style>

