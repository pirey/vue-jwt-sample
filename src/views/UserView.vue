<script>
import axios from 'axios'

export default {
  mounted() {
    const token = localStorage.getItem('token')
    axios.get('http://localhost/api/auth/user-profile', {
      headers: {
        Authorization: `Bearer ${token}`
      }
    }).then(response => {
      this.user = response.data
    })
  },
  data() {
    return {
      user: null
    }
  },
}
</script>
<template>
  <div class="about">
    <h1>User Profile</h1>
    <div v-if="user">
      <div>Name: {{ user.name }}</div>
      <div>Email: {{ user.email }}</div>
    </div>
  </div>
</template>

<style>
</style>
