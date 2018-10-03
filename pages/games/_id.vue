<template>
  <div class="container mx-auto">
    <div>{{ game.name }}</div>
    <div>{{ game.publishers[0].name }}</div>
    <img :src="game.cover.url.replace('t_thumb', 't_cover_big')" alt="cover">
    <p>{{ game.summary }}</p>
    <div>{{ game.platforms }}</div>
    <div>{{ game.first_release_date }}</div>
    <div>{{ game.websites }}</div>
    <div>{{ game.total_rating }}</div>
    <div>{{ game.screenshots }}</div>
    <img v-for="(screenshot, index) in game.screenshots" :key="index" :src="screenshot.url.replace('t_thumb', 't_cover_big')" alt="screenshot">
  </div>
</template>

<script>
import axios from 'axios'

export default {
  asyncData ({ params, error }) {
    const proxyurl = 'https://cors-anywhere.herokuapp.com/'

    return axios.get(`${proxyurl}https://api-endpoint.igdb.com/games/${params.id}/?fields=name,publishers.name,cover,summary,platforms.name,first_release_date,websites,total_rating,screenshots&expand=publishers,platforms`)
    .then((res) => {
      return {
        game: res.data[0]
      }
    })
    .catch((e) => {
      console.log(e)
    })
  },
  head() {
    return {
      title: this.game.name + ' | Video Games'
    }
  }
}
</script>
