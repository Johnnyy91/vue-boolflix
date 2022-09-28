<template>
  <main>
    <div class="movieList" v-for="movie in data " :key="movie.id">
    <div class="cardBox">
        {{movie.title}}
    </div>
</div>
  </main>
</template>

<script>
export default {
name : 'MainComponent',
props : {
    data : Array
}
}
</script>

<style lang="scss" scoped>

</style>