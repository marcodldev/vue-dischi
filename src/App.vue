<template>
  <div id="app">
    
    <header >
        <img src="./assets/spotify-logo-png-7053.png" alt="spotifylogo">
    </header>

    <MainComp  v-for="(elem, index) in dataDischi"
          :key="index"
          :card="elem"/>

  </div>
</template>

<script>
import MainComp from './components/MainComp.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    MainComp
  },
  data() {
      return {
        dataDischi: ''
      }
    },
    mounted() {
      this.getDischi();
    },
    methods : {
      getDischi() {
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
          .then((response) => {
            this.dataDischi = response.data.response
          })}
    }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
};

header {

width: 100%;
text-align:start;
background-color: greenyellow;

img {
    width: 60px;
}
}
</style>
