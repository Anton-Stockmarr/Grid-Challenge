<template>
    <div id="buy-list-box">
        <div id="item-list">
            <div v-bind:key="item.id" v-for="item in this.items">
                <Item class="item" v-bind:id="item.id" v-bind:name="item.name" v-bind:cost="item.cost" v-on:addItem="addItem" v-on:removeItem="removeItem"/>
            </div>
        </div>
        <div>
            <h2 class="total-text">Total: {{total}}</h2>
        </div>
    </div>
</template>



<script>
import Item from './Item'

export default {
    name: 'BuyList',
    components: {
        Item
    },
    data() {
      return {
          items: [
              {id: 1, name: "Pants", cost: 10},
              {id: 2, name: "Hat", cost: 5},
              {id: 3, name: "Gloves", cost: 15},
              {id: 4, name: "Shoes", cost: 8},
              {id: 5, name: "Trousers", cost: 22},
              {id: 6, name: "T-shirt", cost: 6},
              {id: 7, name: "Jacket", cost: 28},
              {id: 8, name: "Glasses", cost: 24},
              {id: 9, name: "Cap", cost: 3},
              {id: 10, name: "Sweater", cost: 19},
              {id: 11, name: "Socks", cost: 6},
              {id: 12, name: "Skirt", cost: 10},
],
          selected: [],
          total: 0
        }
    },
    methods: {
        addItem(id, cost) {
            this.selected = [...this.selected, id];
            this.total += cost;
        },
        removeItem(id, cost) {
            this.selected = this.selected.filter(item => item.id != id);
            this.total -= cost;
        }
    }
}
</script>



<style scoped>
#buy-list-box {
    height: calc(100% - 42px);
    background-color: #DCEBA9;
    border: black 1px solid;
    padding: 20px;
}

#item-list {
    box-shadow: 0 0 7px black;
    max-height: 300px;
    overflow: auto;
}

.total-text {
    text-align: center;
    line-height: 50px;
}

</style>