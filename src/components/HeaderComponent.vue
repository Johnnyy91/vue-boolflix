<template>
  <header>
    <div></div>
    <div class="searchNavigation">
        <input type="text" placeholder="Search Movies" v-model="insertText">
        <button @click="$emit('textToSearch', insertText)">Search</button>
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

</style>