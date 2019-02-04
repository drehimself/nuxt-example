<template>
  <div class="font-sans text-black antialiased">
    <navigation></navigation>
    <nuxt/>
  </div>
</template>

<script>
import Navigation from '@/components/Navigation'
import axios from 'axios'

axios.defaults.headers.common['user-key'] = 'd7e6544670a8b6ef4f81dba61c76fe95'
axios.defaults.headers.common['X-Requested-With'] = 'XMLHttpRequest'

export default {
  components: {
    Navigation
  }
}
</script>


