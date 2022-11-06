<template>
  <Header />
  <h3>Hello User , Welcome to Add Resto page</h3>
  <form class="addrestaurant">
    <input type="text" name="name" v-model="restaurant.name" placeholder="please enter resto name" />
    <input type="text" name="contact" v-model="restaurant.contact" placeholder="please enter resto contact" />
    <input type="text" name="address" v-model="restaurant.address" placeholder="please enter address address" />
    <button type="button" v-on:click="addrestaurant">add new restaurant</button>
  </form>
</template>
<script>
import Header from "./Header.vue";
import axios from "axios";
export default {
  name: "Add-vue",
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
   async addrestaurant(){
        const result = await axios.post("http://localhost:3000/resturant",{
            name : this.restaurant.name,
            contact : this.restaurant.contact,
            address : this.restaurant.address
        })
        if(result.status == 201){
            this.$router.push({name : "Home"});
        }
    }
  },
  components: {
    Header,
  },
  mounted() {
    let user = localStorage.getItem("user-info");
    if (!user) {
      this.$router.push({
        name: "SignUp",
      });
    }
  },
};
</script>