<template>
    <div id="search-list-box">
        <input type="text">
        <div></div>
        <Game />
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
          items: [

          ]
      }
    }
}
</script>


<style scoped>
#search-list-box {
    height: 100%;
    border: black 1px solid;
    background-color: #EADFB7;
}
</style>

