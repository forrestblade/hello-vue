<template>
  <div class="search">
      <input type='text' v-on:keyup.enter="() => search(searchTerm)" v-model="searchTerm">
      <button type='submit' v-on:click="() => search(searchTerm)">search</button>  
  </div>
</template>

<script>
export default {
  data () {
    return {
      searchTerm: '',
      data: {
        gifs: []
      }
    }
  },
  name: 'SearchGifs',
  props: {
    placeholder: String
  },
  methods: {
    search: function (search){
      this.searchTerm = search;
      fetch(`https://api.giphy.com/v1/gifs/search?api_key=Z2IU9ynLCIABokBbv8xQE3rzuwZHRWsW&q=${search}&limit=25&offset=0&rating=G&lang=en`)
      .then(res => res.json())
      .then(data => {
        this.data.gifs = [...data.data]
      })
      .then(this.$emit('clicked', this.data)) //eslint-disable-line no-console

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.search{
  margin: 40px 0 0;
}
button {
  margin-left: 10px;
}
</style>
