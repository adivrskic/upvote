<template>
  <div id="app">
    <h1>{{ appName }}</h1>
    <Posts />
  </div>
</template>

<script>
import Posts from './components/Posts.vue'


export default {
  name: 'App',
  data() {
    return {
      appName: 'Upvote!'
    }
  },
  components: {
    Posts
  }
}
</script>

<style>
body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  font-size: 16px;
  margin: 0;
  padding: 0;
  color: darkslategray;
}

h1 {
  margin: 2.5rem auto;
  font-size: 2rem;
  text-transform: uppercase;
  letter-spacing: .08rem;
  text-align: center;
}
</style>
