<template>
    <div id="table-box">
        <table style="width: 75%">
            <colgroup>
                <col span="1" style="width: 20%;">
                <col span="1" style="width: 30%;">
                <col span="1" style="width: 15%;">
                <col span="1" style="width: 10%;">
            </colgroup>
            <tr>
                <th><p>First name</p></th>
                <th><p>Last name</p></th>
                <th><p>Age</p></th>      
            </tr>
                <tr v-bind:key="row.id" v-for="row in rows">
                    <td><p>{{row.firstName}}</p></td>
                    <td><p>{{row.lastName}}</p></td>
                    <td><p>{{row.age}}</p></td>
                    <td class="button-cells"><button @click="deleteRow(row.id)">X</button></td>
            </tr>
        </table>
    </div>
</template>



<script>

export default {
    name: "Table",
    data() {
        return {
            idCounter: 4,
            rows: [{
                id: 1,
                firstName: "Dave",
                lastName: "Russel",
                age: "53"
            },{
                id: 2,
                firstName: "Tracey",
                lastName: "Reynolds",
                age: "39"
            },{
                id: 3,
                firstName: "Tina",
                lastName: "Scott",
                age: "24"
            },{
                id: 4,
                firstName: "Jason",
                lastName: "Walker",
                age: "33"
            },]
        }
    },
    methods: {
        deleteRow(id) {
            this.rows = this.rows.filter(row => row.id != id);
        },
        addRow(person) {
            if (this.rows.length < 10){
                this.idCounter++;
                person.id = this.idCounter;
                this.rows = [...this.rows, person];
            }
        }
    }
}
</script>

<style scoped>
#table-box {
    height: calc(100% - 2px);
    border: black 1px solid;
    background-color: #99AEAD;
}

th,td {
    position: relative;
    border: 1px solid black;
}

td, th{
    padding: 2px 5px;
}

td p {
    word-wrap: break-word;
}

table {
    font-size: 16px;
    table-layout: fixed;
    margin: 30px auto 0;
}

.button-cells {
    border: none;
}

button {
    color: red;
}

</style>
