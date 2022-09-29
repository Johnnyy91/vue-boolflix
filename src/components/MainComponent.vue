<template>
  <main>
    <h2 v-if="movies.length > 0">MOVIES</h2>
    <div v-for="movie in movies" :key="movie.id">
    <h4>TITLE {{movie.title}}</h4>
    <h5>ORIGINAL TITLE {{movie.original_title}}</h5>
    <p class="flag-img">
      LANGUAGE <img :src="viewFlag(movie.original_language)" alt="">
    </p>
    <div>VOTE {{movie.vote_average}}</div>
    </div>

    <h2 v-if="serieTv.length > 0">SERIES TV</h2>
    <div v-for="serie in serieTv" :key="serie.id">
      <h4>TITLE {{serie.name}}</h4>
      <h5>ORIGINAL TITLE {{serie.original_name}}</h5>
      <p class="flag-img">
        LANGUAGE <img :src="viewFlag(serie.original_language)" alt="">
      </p>
      <div>VOTE {{serie.vote_average}}</div>
    </div>
  </main>
</template>

<script>
export default {
name : 'MainComponent',
data(){
  return{
  }
},
props : {
  movies : Array,
  serieTv : Array,
},
methods : {
  viewFlag(flag){
    if(flag === 'en' || flag ==='uk'){
      flag = 'gb'
    }else if(flag === 'ja'){
      flag = 'jp'
    }
    return `https://flagicons.lipis.dev/flags/4x3/${flag}.svg`
    
  }
}
}
</script>

<style lang="scss" scoped>
.flag-img{
  width: 20px;
}
</style>