<template>
    <div id="table-form-box">
        <h2>Add new person to the table:</h2>
        <div>
            <label>First name:</label>
            <input type ="text" v-model="firstName" :class="{inputError: firstNameError}">
        </div>
        <div>
            <label>Last name:</label>
            <input type ="text" v-model="lastName" :class="{inputError: lastNameError}">
        </div>
        <div>
            <label>Age:</label>
            <input type ="number" v-model="age" :class="{inputError: ageError}">
        </div>
        <button id="submit-row" type="submit" @click="addEntry()">Add</button>
    </div>
</template>




<script>
export default {
    name: "TableForm",
    components: {

    },
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
    height: 100%;
    background-color: #BFDAB8;
    border: 1px solid black;
}

#table-form-box div{
    align-content: center;
}

h2 {
    padding: 20px 0;
    line-height: 30px;
    text-align: center;    
}

label {
    line-height: 30px;
    display: inline-block;
    width: 140px;
    text-align: right;
}

#submit-row {
    display: block;
    width: 100px;
    height: 20px;
    margin: 30px auto 0;
    align-content: center;
}

.inputError {
    box-shadow: 0px 0px 10px red;
}

</style>