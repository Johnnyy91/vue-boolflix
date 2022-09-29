<template>
  <main>
    <h2 v-if="movies.length > 0">MOVIES</h2>
     <div class="card-container">
        <div v-for="movie in movies" :key="movie.id" class="card">
         <img :src="`http://image.tmdb.org/t/p/w342/${movie.poster_path}`" alt="movie" class="poster-img">
         <h4>TITLE: {{movie.title}}</h4>
         <h5>ORIGINAL TITLE: {{movie.original_title}}</h5>
         <p class="flag-img"> LANGUAGE: 
          <img :src="viewFlag(movie.original_language)" alt="movie">
         </p>
         <div>VOTE:
          <i v-for="star in 5" :key="star" class="fa-star"
             :class="changeVote(movie.vote_average) >= star? 'fa-solid':'fa-regular'">
          </i>
         </div>
        </div>
     </div>

    <h2 v-if="serieTv.length > 0">SERIES TV</h2>
    <div class="card-container">
     <div v-for="serie in serieTv" :key="serie.id" class="card">
       <img :src="`http://image.tmdb.org/t/p/w342/${serie.poster_path}`" alt="serieTv" class="poster-img">
       <h4>TITLE: {{serie.name}}</h4>
       <h5>ORIGINAL TITLE: {{serie.original_name}}</h5>
       <p class="flag-img">LANGUAGE: 
        <img :src="viewFlag(serie.original_language)" alt="">
       </p>
       <div>VOTE: 
        <i v-for="star in 5" :key="star" class="fa-star"
        :class="changeVote(serie.vote_average) >= star? 'fa-solid':'fa-regular'">
       </i>
       </div>
     </div>
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
    
  },
  changeVote(vote){
    let result = Math.floor(vote / 2)
    return result
  }
}
}
</script>

<style lang="scss" scoped>
main{
    background-color: rgb(48 48 48);
    color: white;
  }
.flag-img{
  width: 20px;
}
h4{
  width: 200px;
}
.card-container{
  display: flex;
  flex-wrap: wrap;
  column-gap: 30px;
}
.card{
  border: 2px solid black;
  width: 300px;
  padding: 20px;
  margin: 10px;
}
.poster-img{
  width: 150px;
}
</style>


