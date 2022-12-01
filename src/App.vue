<template>
  <div id="app">
    
    <header >
        <img src="./assets/spotify-logo-png-7053.png" alt="spotifylogo">
        <SearchComp @emit1="emitM"/>
        <select name="" id="" v-model="valueOptionSelected">
          <option :value="elem" v-for="(elem,index) in arrayGeneri" :key="index">{{elem}}</option>
        </select>
        
    </header>

    <main >
      <div class="container-fluid">
        <div class="d-flex justify-content-center flex-wrap p-5 customg">
          <MainComp  v-for="(elem, index) in dataDischi"
          :key="index"
          />
        </div>

      </div>


  
    </main>


  </div>
</template>

<script>
import MainComp from './components/MainComp.vue'
import axios from 'axios'
import SearchComp from './components/SearchComp.vue';

export default {
  name: 'App',
  components: {
    MainComp,
    SearchComp
},
  data() {
      return {
        dataDischi: '',
        emitVar : '',
        arrayGeneri: [],
        albums: [],
      }
    },
    computed: {

      funComputed () {
      if (this.sceltaUtente == '') {
        return this.albums
        
      } else {
        return this.albums.filter((elem) => {
          return elem.genre == this.sceltaUtente
        })
        
      }}
    },
    mounted() {
      this.getDischi();
    },
    methods : {
      getDischi() {
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
          .then((response) => {
            this.dataDischi = response.data.response

            this.dataDischi.forEach((singoloAlbum) => {
              if (!this.arrayGeneri.includes(singoloAlbum.genre)) {
                this.arrayGeneri.push(singoloAlbum.genre)
              }
            })

            this.$emit('emit1',this.arrayGeneri)

          })},
          emitM (valoreEmit) {
            this.emitVar = valoreEmit
          }
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
background-color: #424242;

img {
    width: 60px;
    padding: 5px;
}
}

main {
  background-color: #1E2D3B;
  height: 80%;
}

.customg {
  gap: 20px;
}

</style>
