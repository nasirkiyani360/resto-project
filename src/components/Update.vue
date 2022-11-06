<template>
    <Header/>
    <h3>Hello User , Welcome to update resto page</h3>
    <form class="addrestaurant">
    <input type="text" name="name" v-model="restaurant.name" placeholder="please enter resto name" />
    <input type="text" name="contact" v-model="restaurant.contact" placeholder="please enter resto contact" />
    <input type="text" name="address" v-model="restaurant.address" placeholder="please enter address address" />
    <button type="button" v-on:click="updaterestaurant">Update Restaurant</button>
  </form>
</template>
<script>
import Header from './Header.vue'
import axios from 'axios';
export default{
    name : "Update-vue",
    components : {
        Header
    },
    data() {
    return {
        restaurant :{
            name : '',
            contact : '',
            address : ''
        }
    };
  },
  methods:{
   async updaterestaurant(){
        const result = await axios.put("http://localhost:3000/resturant/"+ this.$route.params.id,{
            name : this.restaurant.name,
            contact : this.restaurant.contact,
            address : this.restaurant.address
        })
        if(result.status == 200){
            this.$router.push({name : "Home"});
        }
    }
  },
  async mounted(){
        let user = localStorage.getItem("user-info");
        if(!user){
            this.$router.push({
                name : "SignUp"
            });
        }
        const result = await axios.get("http://localhost:3000/resturant/"+ this.$route.params.id)
        this.restaurant = result.data;
    }
}
</script>