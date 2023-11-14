<template>
  <div class="main">
    <pre>
      <h1>{{ msg }}</h1>
    </pre>

    <div class="ui card">
      <div class="image rounded">
        <img :src="simpleUser.picture.large">
      </div>
      <div class="content">
        <div class="description">
          <p id="user_title">Hi, My name is</p>
          <h3 id="user_value">{{ fullName }}</h3>
        </div>
        <div class="extra content">
          <ul class="content__list">
            <li class="content__list-item">
              <i class="user circle icon active" data-title="Hi, My name is" :data-value="fullName" @mouseover="mouseOver"></i>
            </li>
            <li class="content__list-item">
              <i class="envelope icon" data-title="My email address is" :data-value="simpleUser.email" @mouseover="mouseOver"></i>
            </li>
            <li class="content__list-item">
              <i class="calendar alternate icon" data-title="My birthday is" :data-value="dob" @mouseover="mouseOver"></i>
            </li>
            <li class="content__list-item">
              <i class="map icon" data-title="My address is" :data-value="fullAddress" @mouseover="mouseOver"></i>
            </li>
            <li class="content__list-item">
              <i class="mobile alternate icon" data-title="My phone number is" :data-value="simpleUser.phone" @mouseover="mouseOver"></i>
            </li>
            <li class="content__list-item">
              <i class="user secret icon" data-title="My password is" :data-value="simpleUser.login.password" @mouseover="mouseOver"></i>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

import moment from 'moment'

export default {
  name: 'UserCard',
  props: {
    msg: String,
    user: Array
  },
  data () {
    return {
      simpleUser: this.user[0]
    }
  },
  methods: {
    format_date(value){
      if (value) {
        return moment(String(value)).format('MM/DD/YYYY')
      }
    },
    mouseOver(e) {
      document.getElementById("user_title").textContent=e.target.getAttribute("data-title")
      document.getElementById("user_value").textContent=e.target.getAttribute("data-value")
      Array.from(document.querySelectorAll('.icon')).map(x => x.classList.remove('active'))
      e.target.classList.add('active')
    }
  },
  computed: {
    fullName () {
      return `${this.simpleUser.name.first} ${this.simpleUser.name.last}`
    },
    fullAddress () {
        return `${this.simpleUser.location.street.number} ${this.simpleUser.location.street.name}`
    },
    dob () {
      return this.format_date(this.simpleUser.dob.date)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>

.main {
  display: flex;
  flex-direction: column;
  align-items: center;

  .ui.card {
    width: 600px;

    .image {
      width: 200px;
      position: relative;
      left: 50%;
      top: -20px;
      transform: translateX(-50%);

      &.rounded {
        border-radius: 50% !important;
        overflow: hidden;
      }
    }
  }
}

.description {
  margin-bottom: 40px;
}

#user_value {
  font-size: 25px;
  margin: 10px 25px;
}

.content {
  text-align: center;
}

.content__list {
  display: flex;
  justify-content: center;
  list-style: none;
  padding: 0;

  .icon {
    font-size: 2em;
    margin: 0 10px;
    cursor: pointer;

    &.active {
      color: #83ba43;
      position: relative;

      &:after {
        content: "\f106";
        font-size: 1em;
        position: absolute;
        left: 50%;
        top: -100%;
        transform: translateX(-50%);
      }
    }
  }
}

</style>
