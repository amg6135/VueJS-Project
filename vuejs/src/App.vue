<template>
  <!--<img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/> msg here is just a prop-->
  <div id="app">
    {{ user.username }} - {{fullName}}
    <strong>Followers:</strong> {{ followers }}
    <button @click="followUser">Follow</button> <!--@click is the same as v=on-->
  </div>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      followers: 0,
      user: {
        id: 1,
        username: 'Andrea_1996',
        firstName: 'Andrea',
        lastName: 'Gonzalez',
        email: 'agonzalez@email.com',
        isAdmin: true
      }
    }
  },
  watch: {
    followers(newFollowerCount, oldFollowerCount) {
      if (oldFollowerCount < newFollowerCount) {
        console.log(`${this.user.username} has gained a follower!`)
      }
    }
  },
  computed: {
    fullName () {
      return `${this.user.firstName} ${this.user.lastName}`;
    }
  },
  methods: {
    followUser() {
        this.followers++
    }
  },
  mounted() {
    this.followUser();
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
