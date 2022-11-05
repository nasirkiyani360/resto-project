<template>
    <Header/>
    <h3>Hello User , Welcome to Add Resto page</h3>
</template>
<script>
import Header from './Header.vue'
export default{
    name : "Add-vue",
    components : {
        Header
    },
    mounted(){
        let user = localStorage.getItem("user-info");
        if(!user){
            this.$router.push({
                name : "SignUp"
            });
        }
    }
}
</script>