<template>
    <div id="search-list-box">
        <input type="text" id="search-list-bar" placeholder="search..." v-model="searchKey">
        <div id="search-result-box">
            <Games v-bind:searchKey="searchKey" v-bind:type="'list'"/>
        </div>
    </div>
</template>

<script>
import Games from './Games'


export default {
    name: 'SearchList',
    components: {
        Games
    },
    data() {
      return {
          searchKey: '',
        }
    }
}
</script>

<style scoped>
#search-list-box {
    height: calc(100% - 2px);
    border: black 1px solid;
    background-color: #EADFB7;
}

#search-list-bar {
    font-size: 24px;
    display: block;
    width: calc(90% - 24px);
    margin: 20px auto;
    padding: 5px 10px;
    height: 40px;
}

#search-result-box {
    width: 90%;
    margin: 0 auto 30px;
    height: 300px;
}

</style>

