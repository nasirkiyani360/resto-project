<template>
    <h3>Hello User , Welcome to home page</h3>
</template>
<script>
export default{
    name : "Home-vue",
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