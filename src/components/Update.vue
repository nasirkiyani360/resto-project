<template>
    <Header/>
    <h3>Hello User , Welcome to update resto page</h3>
</template>
<script>
import Header from './Header.vue'
export default{
    name : "Update-vue",
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