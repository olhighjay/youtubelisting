<template>
  <div>
    <input v-model="searchValue" type="text" name="" id="" @input="inputSearch">
  </div>
</template>

<script>

export default {
  name : 'SearchBar',
  data () {
    return {
      searchValue : ''
    }
  },
  methods : {
    inputSearch() {
      this.$emit('termchange', this.searchValue);
    }
  }
  
}
</script>

<style scoped>
  input{
    width: 75%;
  }
  div{
    text-align: center;
    margin: 20px;
  }
</style>