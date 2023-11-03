<template>
  <UserCard msg="Welcome to User Profile pet project" :user="user"/>
</template>

<script>
import UserCard from './components/UserCard.vue'
import axios from 'axios'

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
  mounted () {
    axios
        .get('https://randomuser.me/api/')
        .then(response => (this.user = response))
    // const res = await fetch('https://randomuser.me/api/')
    // const user = await res.json()
  }
}
</script>

<style>
@import 'https://cdnjs.cloudflare.com/ajax/libs/semantic-ui/2.4.1/semantic.min.css';
</style>
