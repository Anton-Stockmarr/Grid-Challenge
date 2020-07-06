<template>
    <div id="item" @click="toggleItem()" :class="{selected: this.selected}">
        <h1 id="item-name">{{name}}</h1>
        <h1 id="item-cost">{{cost}}</h1>
    </div>
</template>



<script>
export default {
    name: 'Item',
    props: ["id","name","cost"],
    data() {
      return {
          selected: false
        }
    },
    methods: {
        toggleItem() {
            this.selected = !this.selected;
            if (this.selected) {
                this.$emit("addItem",this.id, this.cost);
            } else {
                this.$emit("removeItem",this.id, this.cost);    
            }

        }
    }
}
</script>



<style scoped>

#item {
    cursor: pointer;
    background-color: white;
    border: 1px black solid;
    height: 40px;
    padding: 0 10px;
}

.selected {
    background-color: lightblue !important;
}

#item-name {
    display: block;
    float: left;
}

#item-cost {
    display: block;
    float: right;
}

#item h1 {
    line-height: 40px;
}


</style>