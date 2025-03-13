<template>
  <div>
    <h1>Dashboard</h1>
    <p>Welcome, {{ user?.name || 'User' }}!</p>
    <button @click="logout">Logout</button>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      user: null
    };
  },
  async mounted() {
    const token = localStorage.getItem('token');
    if (!token) {
      this.$router.push('/login');
      return;
    }
    try {
      const response = await axios.post('http://localhost:8080/api/auth/me', {}, {
        headers: { Authorization: `Bearer ${token}` }
      });
      console.log(response.data);
      this.user = response.data;
    } catch (error) {
      localStorage.removeItem('token');
      this.$router.push('/login');
    }
  },
  methods: {
    async logout() {
      const token = localStorage.getItem('token');
      await axios.post('http://localhost:8080/api/auth/logout', {}, {
        headers: { Authorization: `Bearer ${token}` }
      });
      localStorage.removeItem('token');
      this.$router.push('/login');
    }
  }
};
</script>