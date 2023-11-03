<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div class="ui card">
      <div class="image">
        <img src="">
      </div>
      <div class="content">
        <a class="header">Kristy</a>
        <div class="meta">
          <span class="date">Joined in 2013</span>
        </div>
        <div class="description">
          Kristy is an art director living in New York.
        </div>
      </div>
      <div class="extra content">
        <a>
          <i class="user icon"></i>
          22 Friends
        </a>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'UserCard',
  props: {
    msg: String,
    user: Object
  },
  mounted () {
    console.log(this.user)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
