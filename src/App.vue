<script>
import axios from 'axios'
import { RouterLink, RouterView } from 'vue-router'

export default {
  mounted() {
    this.token = localStorage.getItem('token')
  },
  data() {
    return {
      token: localStorage.getItem('token')
    }
  },
  methods: {
    logout() {
      localStorage.removeItem('token')
      location.assign('/login')
    }
  }
}

</script>

<template>
  <header>
    <div class="wrapper">
      <nav v-if="token">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/user">User</RouterLink>
        <button @click="logout">logout</button>
      </nav>
      <div v-else>
        Please login
      </div>
    </div>
  </header>

  <RouterView />
</template>

<style>

</style>
