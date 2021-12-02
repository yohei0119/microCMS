<template>
  <ul>
    <li v-for="content in contents" :key="content.id">
      <nuxt-link :to="`/${content.id}`">
        {{ content.title }}
      </nuxt-link>
    </li>
  </ul>
</template>

<script>
export default {
  async asyncData({ $axios }) {
		const data = await $axios.$get(
      'https://sample0119.microcms.io/api/v1/blog',
      {
        headers: { 'X-MICROCMS-API-KEY': process.env.API_KEY }
      }
    );
    return data
	}
}
</script>