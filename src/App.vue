<template>
  <div id="app">
        <div class="wrapper">
          <div id="clock">
            <Clock />
          </div>
          <div id="login">
            <Login />
          </div>
          <div id="quiz">
            <Quiz />
          </div>
          <div id="table">
            <Table ref="table"/>
          </div>
          <div id="table-form">
            <TableForm v-on:addEntry="addPersonToTable"/>
          </div>
          <div id="buy-list">
            <BuyList/>    
          </div>
          <div id="search-list-box">
            <SearchList />          
          </div>
        <div id="search-grid-box">
            <SearchGrid />
        </div>
        <div id="eight-ball-box">
            <EightBall />
        </div>
    </div>
  </div>
</template>

<script>
import Clock from './components/Clock'
import Login from './components/Login'
import Quiz from './components/Quiz'
import Table from './components/Table'
import TableForm from './components/TableForm'
import BuyList from './components/BuyList'
import SearchList from './components/SearchList'
import SearchGrid from './components/SearchGrid'
import EightBall from './components/EightBall'


export default {
  name: 'App',
  components: {
    Clock,
    Login,
    Quiz,
    Table,
    TableForm,
    BuyList,
    SearchList,
    SearchGrid,
    EightBall
  },
  methods: {
    addPersonToTable(person) {
      console.log(this.$refs);
      this.$refs.table.addRow(person);
    }
  }
}
</script>

<style>
  @import "reset.css";

  button {
    cursor: pointer;
}


.wrapper{
    width: calc(100% - 2em);
    margin: 1em;
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-auto-rows: 1fr;
    grid-gap: 10px;
}


</style>
