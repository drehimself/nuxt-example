<template>
  <div class="container mx-auto">
    <div class="game-container">
      <nuxt-link :to="'/games/' + game.id" v-for="game in games" :key="game.id" class="block mb-8">
        <img :src="game.cover.url.replace('t_thumb', 't_cover_big')" alt="cover">
        <div>{{ game.name }}</div>
        <div>{{ game.genres[0].name }}</div>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'
import axios from 'axios'

export default {
  components: {
    Logo
  },
  asyncData ({ params, error }) {
    const proxyurl = 'https://cors-anywhere.herokuapp.com/'

    return axios.get(`${proxyurl}https://api-endpoint.igdb.com/games/?fields=name,genres.name,cover,popularity&order=popularity:desc&expand=genres`)
    .then((res) => {
      return {
        games: res.data
      }
    })
    .catch((e) => {
      console.log(e)
    })
  },
  data() {
    return {

    }
  }
}
</script>

<style>

/* Sample `apply` at-rules with Tailwind CSS
.container {
  @apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/

</style>
