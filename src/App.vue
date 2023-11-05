<template>
  <UserCard msg="Welcome to User Profile pet project" :user="user"/>
</template>

<script>
import UserCard from './components/UserCard.vue'

export default {
  name: 'App',
  components: {
    UserCard
  },
  data () {
    return {
      user: null
    }
  },
  methods: {
    async getUser() {
      const response = await fetch('https://randomuser.me/api/');
      this.user = await response.json();
      console.log(this.user);
    }
  },
  created () {
    this.getUser();
  }
}
</script>

<style>
@import 'https://cdnjs.cloudflare.com/ajax/libs/semantic-ui/2.4.1/semantic.min.css';
</style>
