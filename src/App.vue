<template>
  <div id="app">
    <HeaderComponent @textToSearch='inputAssign'/>
    <MainComponent :movies='ArrayMovies' :serieTv='ArraySerieTv'/>
  </div>
</template>

<script>
import axios from 'axios'
import HeaderComponent from '@/components/HeaderComponent.vue'
import MainComponent from './components/MainComponent.vue'

export default {
  name: 'App',
  components: {
    HeaderComponent,
    MainComponent
},
data(){
  return{
    resultInput : '',
    ArrayMovies : [],
    ArraySerieTv : [],
  }
},
  created(){
   
  },
  methods : {
    inputAssign(insertText){
      this.resultInput = insertText

      axios
        .get(`https://api.themoviedb.org/3/search/movie?api_key=4f84838e7f72cd5486a3c0f5685cf054&language=it-IT&query=${this.resultInput}&page=1&include_adult=false`)
        .then((response) => {
          console.log('movie' , response)
          console.log('movie',response.data.results)
          this.ArrayMovies = response.data.results
        })
        axios
          .get(`https://api.themoviedb.org/3/search/tv?api_key=4f84838e7f72cd5486a3c0f5685cf054&language=it-IT&query=${this.resultInput}&include_adult=false`)
          .then ((response) =>{
            console.log('serie tv',response.data.results)
            this.ArraySerieTv = response.data.results
          })
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;

}
</style>
