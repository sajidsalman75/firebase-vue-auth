<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/register">Register</router-link> | 
      <router-link to="/login">Login</router-link>
    </div>
    <router-view />
    <footer>
      <small>&copy; 2019. Developed By Dawood Shahid</small>
    </footer>
  </div>
</template>

<script>
import firebase from "firebase";
export default {
  data: function(){
    return{
      showNav: true,
    }
  },
  mounted(){
    let user = firebase.auth().currentUser;
    if(user){
      this.showNav = false;
    }
    else{
      this.showNav = true;
    }
  }
}
</script>
<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
