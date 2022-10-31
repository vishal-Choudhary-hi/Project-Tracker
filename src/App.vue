<template>
  <navBar/>
  <router-view/>
</template>
<script>
  import navBar from './components/NavBar.vue'
  export default {
    components:{
      navBar,
    }
  }
</script>
<style>
body{
  background: #f2f2f2;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  max-width: 600px;
  margin: 0 auto;
  color: #555;
}
</style>
