<template>
  <header>
    <div></div>
    <div class="searchNavigation">
      <h1>BOOLFLIX</h1>
      <div class="searchbar">
        <input type="text" placeholder="Search Movies" v-model="insertText" @keyup.enter="$emit('textToSearch', insertText)">
        <button @click="$emit('textToSearch', insertText)">Search</button>
    </div>
    </div>
  </header>
</template>

<script>
export default {
name : 'HeaderComponent',
data(){
    return{
        insertText : '',
    }
}
}
</script>

<style lang="scss" scoped>
  header{
    background-color: black;
  }
.searchNavigation{
  display: flex;
  justify-content: space-between;
  align-items: center;
  h1{
    color: red;
    padding: 15px;
    font-size: 3rem;
  };
  input{
    border: none;
  };
  button{
    background-color: red;
    border: none;
  }
}
.searchbar{
  padding: 0 15px;
}
</style>