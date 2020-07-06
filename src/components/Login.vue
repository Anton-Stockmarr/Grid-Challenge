<template>
    <div id="login-box">
            <input v-model="username" class="username" placeholder="username">
            <input v-model="password" type="password" class="password" placeholder="password">
            <button v-on:click="login" class="login">Login</button>
            <span v-if="success===true" class="response" id="login-success">Login successful!</span>
            <span v-if="success===false" class="response" id="login-failure">Login failed!</span>
    </div>
</template>



<script>
export default {
    name: 'Login',
    components: {
    },
    data() {
      return {
        username: '',
        password: "",
        success: ""
        }
    },
    methods: {
        login: function(){
            if (this.username === "username" && this.password === "password"){
                this.success = true;
            } else {
                this.success = false
            }
        }
    }
}
</script>



<style scoped>
#login-box {
    height: calc(100% - 42px);
    border: black 1px solid;
    background-color: #28363D;
    display: grid;
    padding: 20px;
    grid-template-columns: 1fr;
    grid-template-rows: 1fr 1fr 1fr 1fr;
    grid-template-areas:
    "username"
    "password"
    "button"
    "response";
    grid-gap: 20px;
}

#login-box input{
    width: 100%;
    padding: 12px 12px;
    box-sizing: border-box;
    font-size: 32px;
    border: #111 1px solid;
}

#login-box .username {
    grid-area: username;
    
}
#login-box .password {
    grid-area: password;
}
#login-box .login {
    border: #111 1px solid;
    grid-area: button;
    font-size: 32px;
    background-color: #ccc;
}
#login-box .response {
    grid-area: response;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 32px;
}

#login-success {
background-color: green;
}
#login-failure {
background-color: red;
}

</style>