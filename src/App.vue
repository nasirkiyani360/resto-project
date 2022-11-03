<template>
  <img class="logo" src="./assets/resto-logo.png"/>
  <SignUp/>
</template>

<script>
import SignUp from './components/SignUp.vue';

export default {
  name: 'App',
  components :{
    SignUp
  }
}
</script>

<style>
.logo
{
  width: 150px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
