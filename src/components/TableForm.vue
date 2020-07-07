<template>
    <div id="table-form-box">
        <h2>Add new person to the table:</h2>
        <div id="table-form">
            <label>First name:</label>
            <input type ="text" v-model="firstName" :class="{inputError: firstNameError}">
            <label>Last name:</label>
            <input type ="text" v-model="lastName" :class="{inputError: lastNameError}">
            <label>Age:</label>
            <input type ="number" v-model="age" :class="{inputError: ageError}">
        </div>
        <button id="submit-row" type="submit" @click="addEntry()">Add</button>            
    </div>
</template>




<script>
export default {
    name: "TableForm",
    data() {
        return {
            firstName: '',
            lastName: '',
            age: '',
            firstNameError: false,
            lastNameError: false,
            ageError: false
        }
    },
    methods: {
        addEntry: function() {
            let valid = true;
            if (this.firstName==''){
                this.firstNameError = true;
                valid = false;
            } else {
                this.firstNameError = false;
            }
            if (this.lastName==''){
                this.lastNameError = true;
                valid = false;
            } else {
                this.lastNameError = false;
            }
            if (this.age==''){
                this.ageError = true;
                valid = false;
            } else {
                this.ageError = false;
            }
            if (valid) {
                const Person = {
                    firstName: this.firstName,
                    lastName: this.lastName,
                    age: this.age
                };
                this.$emit("addEntry",Person);
                this.firstName = "";
                this.lastName = "";
                this.age = "";
            }
        }
    }
}
</script>



<style scoped>

#table-form-box {  
    height: calc(100% - 2px);
    background-color: #BFDAB8;
    border: 1px solid black;
}

#table-form {
    display: grid;
    margin: 0 10%;
    grid-template-columns: 1fr 1fr;
    grid-gap: 10px;
}


h2 {
    text-align: center;
    padding: 20px 0;
    line-height: 30px;
}


label {
    line-height: 30px;
    display: block;
}

input {
    width: calç(100% - 4px);
}


#submit-row {
    display: block;
    height: 40px;
    width: 80%;
    margin: 20px 10%;
}
.inputError {
    box-shadow: 0px 0px 10px red;
}

</style>