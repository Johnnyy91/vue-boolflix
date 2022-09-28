<template>
  <div id="app">
    <HeaderComponent @textToSearch='inputAssign'/>
  </div>
</template>

<script>
import axios from 'axios'
import HeaderComponent from '@/components/HeaderComponent.vue'

export default {
  name: 'App',
  components: {
    HeaderComponent,
},
data(){
  return{
    resultInput : '',
  }
},
  created(){
   
  },
  methods : {
    inputAssign(insertText){
      this.resultInput = insertText

      axios
        .get(`https://api.themoviedb.org/3/search/movie?api_key=4f84838e7f72cd5486a3c0f5685cf054&language=en-US&query=${this.resultInput}&page=1&include_adult=false`)
        .then((response) => {
          console.log(response)
          console.log(response.data.results)
        })
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
</style>
