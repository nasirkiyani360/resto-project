<template>
  <Header />
  <h3>Hello {{ name }} , Welcome to home page</h3>
  <div>
    <table border="1">
      <tr>
        <td>Id</td>
        <td>name</td>
        <td>contact</td>
        <td>address</td>
        <td>Actions</td>
      </tr>
      <tr v-for="item in restaurant" :key="item.id">
        <td>{{ item.id }}</td>
        <td>{{ item.name }}</td>
        <td>{{ item.contact }}</td>
        <td>{{ item.address }}</td>
        <td>
          <router-link :to="'/update/' + item.id">Update</router-link>
          <button v-on:click="deleteRestaurant(item.id)">Delete</button>
        </td>
      </tr>
    </table>
  </div>
</template>
<script>
import axios from "axios";
import Header from "./Header.vue";
export default {
  name: "Home-vue",
  data() {
    return {
      name: "",
      restaurant: [],
    };
  },
  components: {
    Header,
  },
  methods: {
   async deleteRestaurant(id) {
      const result =await axios.delete("http://localhost:3000/resturant/" + id);
      if (result.status == 200) {
        this.loadData();
      }
    },
    async loadData() {
      let user = localStorage.getItem("user-info");
      if (user != null) {
        this.name = JSON.parse(user).name;
      }
      if (!user) {
        this.$router.push({
          name: "SignUp",
        });
      }
      let result = await axios.get("http://localhost:3000/resturant");
      this.restaurant = result.data;
    },
  },
  async mounted() {
    this.loadData();
  },
};
</script>
<style>
td {
  width: 160px;
  height: 40px;
}
</style>