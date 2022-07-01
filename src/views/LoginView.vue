<script>
import axios from 'axios'

export default {
  data() {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    submit() {
      axios.post('http://localhost/api/auth/login', {
        email: this.email,
        password: this.password
      }).then(response => {
        localStorage.setItem('token', response.data.access_token)
        location.assign('/')
      })
    }
  }
}
</script>
<template>
  <div class="about">
    <h1>Login</h1>
    <form @submit.prevent="submit">
      <div>
        <div>email</div>
        <div><input v-model="email" /></div>
      </div>
      <div>
        <div>password</div>
        <div><input v-model="password" type="password" /></div>
      </div>
      <div>
        <button type="submit">login</button>
      </div>
    </form>
  </div>
</template>

<style>
</style>
