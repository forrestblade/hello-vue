<template>
  <div class="fl pa2 w-50 w-20-ns"> 
    <a :href=href class="db aspect-ratio aspect-ratio--1x1 dim">
      <span v-bind:style="{ backgroundImage: `url(${src})` }" class="bg-center cover aspect-ratio--object">
      </span>
    </a>
  </div>
</template>

<script>
export default {
  name: 'GifImages',
  props: {
    key: String,
    href: String,
    src: String,
    title: String
  }
}
</script>
