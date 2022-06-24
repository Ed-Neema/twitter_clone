<template>
  <div id="app">
    {{ user.username }} - {{ fullName }}

    <strong>Followers: </strong> {{ followers }}
    <button v-on:click="followUser()">Follow</button>

  </div>
</template>

<script>



export default {
  name: 'App',
  data() {
    return {
      followers: 0,
      user: {
        id: 1,
        username: '@_edmucious',
        firstName: "Ednah",
        lastName: "Akoth",
        isAdmin: true
      }
    }
  },

  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`
    }
  },

  methods: {

    followUser() {
      this.followers++
    },
    

  },
  mounted() {
    this.followUser();
  },
  watch: {
    followers(newFollowerCount, oldFollowerCount){
       if(oldFollowerCount < newFollowerCount){
        console.log(`${this.user.username} has gained a follower`)
       }
    }

  },


  components: {

  }
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  color: #2c3e50;
  display: flex;
  flex-direction: column;
  align-items: center;

}

button {
  cursor: pointer;
  display: inline-block;
  background: #333;
  color: white;
  font-size: 18px;
  border: 0;
  padding: 1rem 1.5rem;
}
</style>
