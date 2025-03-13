<template>
  <div>
    <h1>Register</h1>
    <form @submit.prevent="register">
      <input v-model="form.name" placeholder="Name" required />
      <input v-model="form.email" type="email" placeholder="Email" required />
      <input v-model="form.password" type="password" placeholder="Password" required />
      <input v-model="form.password_confirmation" type="password" placeholder="Confirm Password" required />
      <button type="submit">Register</button>
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
        name: '',
        email: '',
        password: '',
        password_confirmation: ''
      },
      message: ''
    };
  },
  methods: {
    async register() {
      try {
        const response = await axios.post('http://localhost:8080/api/auth/register', this.form);
        this.message = response.data.message;
        this.$router.push('/login');
      } catch (error) {
        this.message = error.response?.data?.message || 'Registration failed';
      }
    }
  }
};
</script>