<template>
  <main>
    <h2 v-if="movies.length > 0">MOVIES</h2>
     <div class="card-container">
        <div v-for="movie in movies" :key="movie.id" class="card">
         <img :src="`http://image.tmdb.org/t/p/w342/${movie.poster_path}`" alt="movie" class="poster-img">
         <div class="text-information">
          <h4>TITLE: {{movie.title}}</h4>
          <h5>ORIGINAL TITLE: {{movie.original_title}}</h5>
          <p class="flag-img"> LANGUAGE:
            <img :src="viewFlag(movie.original_language)" alt="movie">
          </p>
          <div>VOTE: <i v-for="star in 5" :key="star" class="fa-star"
              :class="changeVote(movie.vote_average) >= star? 'fa-solid':'fa-regular'">
            </i>
          </div>
         </div>
        </div>
     </div>

     <h2 v-if="serieTv.length > 0">SERIES TV</h2>
      <div class="card-container">
        <div v-for="serie in serieTv" :key="serie.id" class="card">
         <img :src="`http://image.tmdb.org/t/p/w342/${serie.poster_path}`" alt="serieTv" class="poster-img">
         <div class="text-information">
          <h4>TITLE: {{serie.name}}</h4>
          <h5>ORIGINAL TITLE: {{serie.original_name}}</h5>
          <p class="flag-img">LANGUAGE:
            <img :src="viewFlag(serie.original_language)" alt="">
          </p>
          <div>VOTE: <i v-for="star in 5" :key="star" class="fa-star"
              :class="changeVote(serie.vote_average) >= star? 'fa-solid':'fa-regular'">
            </i>
          </div>
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

h2{
  color: red;
  font-size: 2rem;
  padding: 20px;
}

.flag-img{
  width: 20px;
  display: flex;
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
  position: relative;
  &.card:hover .text-information{
    opacity: 1;
  }
}

.text-information{
  width: calc(100% - 40px);
  height: calc(100% - 40px);
  padding: 0px 10px;
  font-size: 1.5rem;
  position: absolute;
  top: 20px;
  left: 20px;
  opacity: 0;
  background-color: black;
  h4,h5,p{
    padding: 15px 0;
  }
}

.poster-img{
  width: 100%;
  height: 400px;
}

.fa-star{
  color: rgb(242, 242, 40);
}
</style>


