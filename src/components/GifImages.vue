<template>
  <div :key=key class="fr w-50 w-25-m w-20-l pa2"> 
    <a :href=href class="db link dim tc">
      <img :src=src class="w-100 db outline black-10" />
      <dl class="mt2 f6 lh-copy">
        <dt class="clip">Title</dt>
        <dd title='title' class="ml0 black truncate w-100">{{title}}</dd>
      </dl>
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
  },
  methods: {
    }
  }

</script>
