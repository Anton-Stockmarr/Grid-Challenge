<template>
    <div id="search-grid-box">
        <div id="search-grid-bar">
            <input type="text" placeholder="search..." v-model="searchKey">
            <button @click="toggleGrid()">{{type}}</button>
        </div>
        <div id="search-result-box">
            <Games v-bind:searchKey="searchKey" v-bind:type="type"/>
        </div>
    </div>
</template>

<script>
import Games from './Games'


export default {
    name: 'SearchGrid',
    components: {
        Games
    },
    data() {
      return {
          searchKey: '',
          type: 'grid'
        }
    },
    methods: {
        toggleGrid() {
            console.log("toggled");
            if (this.type === 'grid') {
                this.type = 'list';
            } else {
                this.type = 'grid';
            }
        }
    }
}
</script>


<style scoped>
#search-grid-box {
    height: calc(100% - 2px);
    border: black 1px solid;
    background-color: #DFC58D;
}

#search-grid-bar {
    display: block;
    width: 90%;
    margin: 20px auto;
    height: 54px;
}

#search-grid-bar input{
    font-size: 24px;
    display: block;
    float: left;
    padding: 5px 10px;
    width: calc(100% - 24px - 54px - 20px);
    height: calc(100% - 14px);
}

#search-grid-bar button {
    display: block;
    float: right;
    width: 54px;
    height: 54px;
}


#search-result-box {
    width: 90%;
    margin: 0 auto 30px;
    height: 300px;
}
</style>

