<template>
  <UserCard msg="Welcome to User Profile pet project" v-if="user" :user="user"/>
  <div class="button-wrapper">
    <button type="button" @click="getUser" class="button align-center">Fetch New User</button>
  </div>
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
      const response = await fetch('https://randomuser.me/api/')
      .then((res) => res.json())
      .then((user) => user.results)
      // Sending Single User
      this.user =  response[0];
    }
  },
  created () {
    this.getUser();
  }
}
</script>

<style >
@import 'https://cdnjs.cloudflare.com/ajax/libs/semantic-ui/2.4.1/semantic.min.css';
* {
  transition: all 250ms ease-in;
}
</style>

<style lang="scss">
.button-wrapper {
  text-align: center;
}
.button {
  display: inline-block;
    margin: 10px 0;
    border: 1px solid #d4d4d5;
    background-color: #fff;
    padding: 10px 15px;
    border-radius: 10px;
    cursor: pointer;

    &:hover {
      color: #83ba43;
      color: #fff;
    }
}
</style>
