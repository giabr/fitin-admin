<template>
  <div class="container login">
      <form class="form-signin" @submit.prevent="login">
        <img src="../assets/logo-bold.png" alt="">
        <h4>Fitin Admin</h4>
        <label for="inputUsername" class="sr-only">Username</label>
        <input v-model="username" type="username" id="inputUsername" class="form-control" placeholder="Username" required autofocus>
        <label for="inputPassword" class="sr-only">Password</label>
        <input v-model="password" type="password" id="inputPassword" class="form-control" placeholder="Password" required>
        <button class="btn btn-lg btn-primary btn-block" type="submit">Sign in</button>
      </form>
  </div>
</template>

<script>

export default {
    data: function(){
        return{
            username: '',
            password: '',
            token: true
        }
    },
    methods:{
        login(){
            if(this.username === 'admin' && this.password === 'ayamgeprek'){
                this.$router.push({name: 'Admin', params: {token: this.token}})
            } else {
                alert('Wrong Username/Password')
            }
        }
    }
}
</script>

<style>
    .login{
        padding-top: 10%;
    }
    h4{
        text-align: center;
        margin-bottom: 20px;
    }
    img{
        display: block;
        margin-left: auto;
        margin-right: auto;
        margin-bottom: 20px;
    }
    #inputUsername,
    #inputPassword{
        margin-left: 25%;
        margin-bottom: 30px;
        width: 50%;
    }
    .btn{
        width: 20%;
        float: right;
        margin-right: 25%;
    }
</style>