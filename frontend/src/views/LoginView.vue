<template>
  <div>
    <h1>Login</h1>
    <form @submit.prevent="login">
      <input v-model="form.email" type="email" placeholder="Email" required />
      <input v-model="form.password" type="password" placeholder="Password" required />
      <button type="submit">Login</button>
    </form>
    <p>{{ message }}</p>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      form: {
        email: '',
        password: ''
      },
      message: ''
    };
  },
  methods: {
    async login() {
      try {
        const response = await axios.post('http://localhost:8080/api/auth/login', this.form);
        localStorage.setItem('token', response.data.access_token);
        this.message = response.data.message;
        this.$router.push('/dashboard');
      } catch (error) {
        this.message = error.response?.data?.message || 'Login failed';
      }
    }
  }
};
</script>