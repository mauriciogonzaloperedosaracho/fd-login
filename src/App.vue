<template>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link> |
    <router-link to="/login">Login</router-link> |
    <button v-if="isLoggedIn" @click="logout()" class="btn btn-danger">Logout</button>
  </nav>
  <router-view/>
</template>


<script>

  export default {
    data(){
      return{
        isLoggedIn: false,
        
      }
    },
    created() {
      if(localStorage.getItem('accessToken') === "undefined"){
        
        localStorage.removeItem('accessToken')
      }
      if(localStorage.getItem('accessToken')){
        this.isLoggedIn = true
        console.log(this.isLoggedIn)
      }
    },
    methods:{
      logout(){
        localStorage.removeItem('accessToken')
        window.location.href = '/login'
      }
    }
  }
  </script>
  
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
