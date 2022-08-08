// pages/index.vue

<template>
  <ul>
    <li v-for="content in contents" :key="content.id">
      <nuxt-link :to="`/${content.id}`">{{ content.title }}</nuxt-link>
    </li>
  </ul>
</template>
<script>
import axios from 'axios'
export default {
  async asyncData({ params }) {
    const page = params.p || '1'
    const limit = 10
    const { data } = await axios.get(
      `https://ay24h.microcms.io/api/v1/blogs?limit=${limit}&offset=${(page - 1) * limit}`,
      { headers: { 'X-MICROCMS-API-KEY': '29d3c811bb1140db93c8e350f53e6aa7e3d2' } }
    )
    return data
  }
}
</script>

