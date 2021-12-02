<template>
  <main>
    <h1>{{ title }}</h1>
    <p>{{ publishedAt }}</p>
    <p>{{ category && category.name }}</p>
    <div v-html="body"></div>
  </main>
</template>

<script>
export default {
  async asyncData({ $axios, params }) {
		const data = await $axios.$get(
      `https://sample0119.microcms.io/api/v1/blog/${params.id}`,
      {
        headers: { 'X-MICROCMS-API-KEY': process.env.API_KEY }
      }
    );
    return data
	}
}
</script>