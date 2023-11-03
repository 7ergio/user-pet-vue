<template>
  <UserCard msg="Welcome to User Profile pet project"/>
</template>

<script>
import UserCard from './components/UserCard.vue'

export default {
  name: 'App',
  components: {
    UserCard
  }
}
</script>

<style>
@import 'https://cdnjs.cloudflare.com/ajax/libs/semantic-ui/2.4.1/semantic.min.css';
</style>
