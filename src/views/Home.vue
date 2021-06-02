<template>
  <div class="home">
    <BaseHeader />
    <main class="container">
      <BaseInput
        v-model="textFilter"
        name="searchGif"
        placeholder="Escribe nombre gif"
        @keyup-enter="searchGifs(textFilter)"
      />
      <BaseButton text="Buscar" @click="searchGifs(textFilter)" />
      <GifsList v-if="searchedGifs.length" :gifs="searchedGifs" />
      <GifsList
        :gifs="gifs"
        title="Trending gifs"
        @select-gif="navigateToDetail(gifs)"
      />
    </main>
  </div>
</template>

<script>
// @ is an alias to /src
import BaseHeader from '@/components/BaseHeader.vue'
import GifsList from '@/components/GifsList.vue'
import BaseInput from '@/components/BaseInput.vue'
import BaseButton from '@/components/BaseButton.vue'

export default {
  name: 'Home',
  components: {
    BaseHeader,
    GifsList,
    BaseInput,
    BaseButton,
  },
  data() {
    return {
      gifs: [],
      searchedGifs: [],
      textFilter: '',
    }
  },
  created() {
    this.loadData(), this.searchGifs()
  },
  methods: {
    async loadData() {
      const response = await fetch(
        'https://api.giphy.com/v1/gifs/trending?api_key=B74UZGKj9QqKSSUf9aLjWtT8eVnbZ23c&limit=10'
      )
      const { data } = await response.json()

      this.gifs = data
    },

    async searchGifs(value) {
      const response = await fetch(
        `https://api.giphy.com/v1/gifs/search?api_key=B74UZGKj9QqKSSUf9aLjWtT8eVnbZ23c&limit=10&q=${value}`
      )
      const { data } = await response.json()

      this.searchedGifs = data
    },
    navigateToDetail(gifId) {
      this.$router.push({ name: 'GifDetail', params: { id: gifId } })
    },
  },
}
</script>
