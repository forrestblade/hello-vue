<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      Search for gifs here or checkout where
      <a href="https://giphy.com/" target="_blank" rel="noopener"> they come from</a>.
    </p> 
    <SearchGifs @clicked="onChildClick"/>
    <div v-if="gifs.length" class="cf flex flex-wrap pa2">
      <GifImages
        v-for="gif in gifs"
        v-bind:key="gif.id"
        v-bind:src="gif.images.original.url"
        v-bind:title="gif.title"
        v-bind:href="gif.bitly_url"
      />
    </div>
  </div>
</template>

<script>
import SearchGifs from "./SearchGifs";
import GifImages from './GifImages'
export default {

  name: 'HelloWorld',
  data() {
    return {
      gifs: []
    }
  },
  components: {
    SearchGifs,
    GifImages
  },
  props: {
    msg: String
  },
  methods: {
    onChildClick: function (value) {
      this.gifs = value.gifs
    }
  }
}
</script>
