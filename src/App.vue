<template>
  <div id="app">
    <BaseHeader />
    <main class="container">
      <LoginForm />

      <BaseInput
        v-model="textFilter"
        name="searchGif"
        placeholder="Escribe nombre gif"
        @keyup-enter="searchGifs(textFilter)"
      />
      <BaseButton text="Buscar" @click="searchGifs(textFilter)" />
      <GifsList v-if="searchedGifs.length" :gifs="searchedGifs" />
      <GifsList :gifs="gifs" title="Trending gifs" />
    </main>
  </div>
</template>

<script>
import BaseHeader from '@/components/BaseHeader.vue'
import GifsList from '@/components/GifsList.vue'
import BaseInput from '@/components/BaseInput.vue'
import BaseButton from '@/components/BaseButton.vue'
import LoginForm from '@/components/LoginForm.vue'

export default {
  name: 'App',
  components: {
    BaseHeader,
    GifsList,
    BaseInput,
    BaseButton,
    LoginForm,
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
  },
}
</script>
