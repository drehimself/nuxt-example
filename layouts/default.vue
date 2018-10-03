<template>
  <div class="font-sans text-black antialiased">
    <navigation></navigation>
    <nuxt/>
  </div>
</template>

<script>
import Navigation from '@/components/Navigation'
import axios from 'axios'

axios.defaults.headers.common['user-key'] = 'b4c05406ff70bf1f57ff0c5a35d38de4'
axios.defaults.headers.common['X-Requested-With'] = 'XMLHttpRequest'

export default {
  components: {
    Navigation
  }
}
</script>


