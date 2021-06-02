<template>
  <section v-if="gif">
    <h2>{{ gif.title }}</h2>
    <div>
      <img :src="gif.images.original.url" :alt="gif.title" />
      <span>{{ gif.title }}</span>
    </div>
  </section>
</template>

<script>
export default {
  name: 'GifDetail',
  props: {
    id: {
      type: String,
      default: '',
    },
  },
  created() {
    this.loadData()
  },
  methods: {
    async loadData() {
      const response = await fetch(
        `https://api.giphy.com/v1/gifs/${this.id}?api_key=B74UZGKj9QqKSSUf9aLjWtT8eVnbZ23c`
      )
      const { data } = await response.json()

      this.gif = data
    },
  },
}
</script>

<style></style>
