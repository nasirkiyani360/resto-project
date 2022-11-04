<template>
    <h2>Sign Up</h2>
    <div class="register">
        <input type="text" v-model="name" placeholder="Enter Name" />
        <input type="text" v-model="email" placeholder="Enter Email" />
        <input type="password" v-model="password" placeholder="Enter Password" />
        <button v-on:click="signUp" type="submit">Sign Up</button>
    </div>
</template>
<script>

import axios from 'axios';

export default {
    name: 'SignUp',
    data(){
        return{
            name : '',
            email : '',
            password : ''
        }
    },
    methods:{
        async signUp(){
            let result = await axios.post('http://localhost:3000/users',{
                name : this.name,
                email : this.email,
                password : this.password
            })
            if(result.status == "201")
            {
                localStorage.setItem("user-info", JSON.stringify(result.data));
                this.name='';
                this.email='';
                this.password='';
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
<style scoped>
.register input {
    width: 300px;
    height: 40px;
    padding-left: 20px;
    display: block;
    margin-bottom: 30px;
    margin-left: auto;
    margin-right: auto;
    border: 1px solid skyblue;
}

.register button {
    width: 320px;
    height: 40px;
    border: 1px solid skyblue;
    background: skyblue;
    color: #fff;
    cursor: pointer;
}
</style>