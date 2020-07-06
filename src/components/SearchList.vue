<template>
    <div id="search-list-box">
        <input type="text" id="search-bar" placeholder="search..." v-model="searchKey">
        <div id="search-results">
            <div v-bind:key="game.id" v-for="game in games" v-show="inSearch(game.name)">
                <Game v-bind="game"/>
            </div>
        </div>
    </div>
</template>

<script>
import Game from './Game'


export default {
    name: 'SearchList',
    components: {
        Game
    },
    data() {
      return {
          searchKey: '',
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
#search-list-box {
    border: black 1px solid;
    background-color: #EADFB7;
    height: 100%;
}

#search-bar {
    display: block;
    width: calc(90% - 8px);
    margin: 20px auto;
    height: 40px;
}

#search-results {
    box-shadow: 0 0 7px black;
    width: 90%;
    margin: 30px auto;
    max-height: 300px;
    overflow: auto;
}
</style>

