<template>
  <div class="hello">
    <div>
      <form class="box" method="post" @submit.prevent="submitForm">
        <h1>Login</h1>
        <input v-model="form.email" type="text" name="" placeholder="Email">
        <input v-model="form.password" type="password" name="" placeholder="Password">
        <input type="submit" name="" placeholder="Login">
      </form>
    </div>
    <div class="info">
      <div class="min-info">Nie masz konta?</div>
      <NuxtLink to="/register" class="dupa">Załóż konto</NuxtLink>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      form: {
        email: 'a@gmail.com',
        password: 'a123'
      }
    }
  },
  methods: {
    async submitForm () {
      await this.$auth.loginWith('local', {
        data: this.form
      })
      if (this.$auth.loggedIn) {
        this.$router.push('/dashboard')
      }
    }
  }
}
</script>

<style scoped>
body {
  margin: 0;
  padding: 0;
  font-family: sans-serif;
}

.box {
  width: 300px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, 50%);
  text-align: center;
}

.box h1 {
  color: black;
  font-weight: bold;
}

.box input[type="text"],
.box input[type="password"] {
  display: block;
  margin: 20px auto;
  text-align: center;
  border: 2px solid green;
  padding: 14px 10px;
  width: 200px;
  outline: none;
  color: black;
  border-radius: 10px;
  transition: 0.25s;
}

.box input[type="text"]:focus,
.box input[type="password"]:focus {
  border: 2px solid #46de35;
}

.box input[type="submit"] {
  display: block;
  margin: 20px auto;
  text-align: center;
  border: 2px solid green;
  padding: 14px 40px;
  outline: none;
  border-radius: 10px;
  background-color: green;
  color: white;
  transition: 0.25s;
  cursor: pointer;
}

.box input[type="submit"]:hover {
  background-color: #169126;
}

.box input[type="submit"]:active {
  border-radius: 5px;
}

.info {
  position: absolute;
  text-align: center;
  top: 50%;
  left: 50%;
  transform: translate(-50%, 50%);
}

.min_info {
  color: black;
}

.dupa {
  text-decoration: none;
  color: green;
  font-size: 18px;
}
</style>
