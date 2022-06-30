<template>
  <div class="container">
    <h1 class="head">Inforios </h1>
        <nuxt-link class="signup" to="/">Back</nuxt-link>
    <form action="" class="form">
        <label for="">Username</label><br>
        <input class="form-control" type="text" name="" id="" v-model="username"><br>
        <label for="">Password</label><br>
        <input class="form-control" type="text" name="" id="" v-model="password"><br>

        <button @click.prevent="signup()">Sign Up</button>
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
        async signup(){
            if(this.username && this.password){
                const userData = {
                    name: this.username,
                    password: this.password
                }
                await this.$axios.$post('http://192.168.1.27:2000/signup', userData)
                    .then(res => {
                        alert('Signup Success')
                        console.log('SignUp res', res);
                    }).catch(err => {
                        alert('Error')
                        console.log(err);
                    })
            }else {
                alert('Please enter all fields')
            }
        }
    }
}
</script>

<style>

</style>