<template>
  <div id="app">
    <Marquee speed="100" :marqueeList="list" height="100" bg="#f99" fontSize="40"/>
    <img src="./assets/logo.png">
    <router-view/>
  </div>
</template>

<script>
import Marquee from '@/components/Marquee'
export default {
  name: 'App',
  components: {
    Marquee
  },
  data () {
    return {
      list: [
        'info item0',
        'info item1',
        'info item2',
        'info item3'
      ]
    }
  },
  mounted () {
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50; 
  margin-top: 60px;
}
</style>
