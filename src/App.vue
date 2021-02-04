<template>
  <div class="container">
    <Register />
    <Login />
  </div>
</template>

<script>
import Register from './components/Register.vue'
import Login from './components/Login.vue'

export default {
  name: 'App',
  components: {
    Register,
    Login
  }
}
</script>

<style scoped>
.container{
  max-width: 400px;
  margin: 0 auto;
}
</style>
