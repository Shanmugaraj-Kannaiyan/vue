<template>
  <div class="container">
    <h1 class="head">Inforios </h1>
    <p class="signup" @click="signup()">SignUp</p>
    <form action="" class="form">
        <label for="">Username</label><br>
        <input class="form-control" type="text" name="" id="" v-model="username"><br>
        <label for="">Password</label><br>
        <input class="form-control" type="text" name="" id="" v-model="password"><br>

        <button @click.prevent="signin()">Sign In</button>
    </form>
  </div>
</template>

<script>

export default {
  data(){
    return {
      username: '',
      password: ''
    }
  },
  methods: {
    signin(){
            if(this.username && this.password){
                const userData = {
                    name: this.username,
                    password: this.password
                }
                 this.$axios.$post('http://192.168.1.27:2000/signin', userData)
                    .then(res => {
                        this.$nuxt.$router.push({path: '/home'})
                    }).catch(err => {
                        alert('Invalid User')
                        console.log(err);
                    })
            }else {
                alert('Please enter all fields')
            }
    },
    signup(){
      this.$nuxt.$router.push({path: '/signup'})
    }
  }
}
</script>

<style>
.container {
  border: 1px solid black;
  width: 50%;
  margin: auto;
  height: 100%;
}
.head{
  margin: 5px;
  text-align: center;
  font-weight: bold;
  color: chocolate;
  border: 1px solid chocolate;
}
.form{
  margin: 10px;
  width: 50%;
  margin: auto;
  padding: 8px;
  margin-left: 370px;
}
.signup{
  text-align: center;
  text-decoration: none;
}
.signup:hover{
  text-decoration: underline;
}
</style>