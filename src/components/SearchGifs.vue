<template>
  <div class="bg-light-red mw7 center pa4 br2-ns ba b--black-10">
    <fieldset class="cf bn ma0 pa0">
        <label class="clip" for="email-address">Email Address</label>
        <input class="f6 f5-l input-reset bn fl black-80 bg-white pa3 lh-solid w-100 w-75-m w-80-l br2-ns br--left-ns" v-on:keyup.enter="() => search(searchTerm)" v-model="searchTerm" type="text">
        <input class="f6 f5-l button-reset fl pv3 tc bn bg-animate bg-black-70 hover-bg-black white pointer w-100 w-25-m w-20-l br2-ns br--right-ns" type='submit' v-on:click="() => search(searchTerm)" value="search">
    </fieldset>
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
      .then(() => this.$emit('clicked', this.data)) //eslint-disable-line no-console

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
