<template>
  <div>
    <h3>
      <slot>{{ title }}</slot>
    </h3>

    <section class="gifs-wrapper">
      <div v-for="gif in gifs" :key="gif.id" class="gif-element">
        <img
          :src="getImage(gif)"
          :alt="gif.title"
          @click="selectItem(gif.id)"
        />
        <p class="gif-title">{{ gif.title }}</p>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'GifsList',
  props: {
    gifs: {
      type: Array,
      default: () => [], //needs a function, cannot be "default: []"
    },
    title: {
      type: String,
      default: '',
    },
  },
  methods: {
    getImage(item) {
      return item.images.original.url // use a method if you want to pass props, computed is not valid
    },
    selectItem(gifId) {
      this.$emit('select-gif', gifId)
    },
  },
}
</script>

<style lang="scss" scoped>
.gifs-wrapper {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 10px;
  align-items: center;
  padding: 0 4px;
}
.gif-element {
  position: relative;
  display: flex;
  max-width: 250px;
  img {
    width: 100%;
  }
}
.gif-title {
  position: absolute;
  bottom: 0;
  background-color: lightgray;
  padding: 10px;
  margin: 0;
}
</style>
