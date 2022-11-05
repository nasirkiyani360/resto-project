<template>
    <h2>Login</h2>
    <div class="register">
        <input type="text" v-model="email" placeholder="Enter Email" />
        <input type="password" v-model="password" placeholder="Enter Password" />
        <button v-on:click="login" type="submit">Sign Up</button>
        <p><router-link to="/sign-up">SignUp</router-link></p>
    </div>
</template>
<script>
import axios from 'axios';
export default {
    name : "Login-vue",
    data(){
        return{
            email : "",
            password : ""
        }
    },
    methods :{
       async login(){
            let result = await axios.get(`http://localhost:3000/users?emai=${this.email}&password=${this.password}`)
            if(result.status == "200" && result.data.length > 0)
            {
                localStorage.setItem("user-info", JSON.stringify(result.data[0]));
                this.$router.push({
                    name : "Home"
                });
            }
        }
    },
    mounted(){
        let user = localStorage.getItem("user-info");
        if(user){
            this.$router.push({
                name : "Home"
            });
        }
    }
}
</script>