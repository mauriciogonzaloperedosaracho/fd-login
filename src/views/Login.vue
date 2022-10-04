<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div class="about">
    <h1>Login</h1>
    <div class="col-6 mx-auto">
    <form>
  <div class="mb-3">
    <label for="exampleInputEmail1" class="form-label">Email address</label>
    <input type="email" v-model="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
    <div id="emailHelp" class="form-text">We'll never share your email with anyone else.</div>
  </div>
  <div class="mb-3">
    <label for="exampleInputPassword1" class="form-label">Password</label>
    <input type="password" v-model="password" class="form-control" id="exampleInputPassword1">
  </div>
  <div class="mb-3 form-check">
    <input type="checkbox" class="form-check-input" id="exampleCheck1">
    <label class="form-check-label" for="exampleCheck1">Check me out</label>
  </div>
  <button type="submit" @click.prevent="submit()" class="btn btn-primary">Submit</button>
</form>
  </div>
</div>
</template>



<script>

export default {
  data(){
    return{
      email:'',
      password:''
    }
  },
  methods:{
    async submit(){
      console.log(this.email);
      console.log(this.password);

      const requestOptions = {
        method : "POST",
        headers : {
           "Content-type": "application/json",
           "Access-Control-Allow-Origin" : "*"
        },
        body : JSON.stringify({email: this.email, password: this.password})
      }
      

      fetch("http://localhost:3000/auth/signin/", requestOptions)
        
    
      .then(response => response.json())

      .then(data => {
        console.log(data.accessToken)
        localStorage.setItem('accessToken', data.accessToken)
        window.location.href = '/'
      })

    }
  }
}
</script>
