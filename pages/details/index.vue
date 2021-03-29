<template>
  <div>
    <ul v-for="post in posts" :key="post.id">
      <NuxtLink :to="`${post.title.toLowerCase()}/${post.slug}`">
        <li>{{ posts.title }}</li>
      </NuxtLink>
    </ul>
  </div>
</template>
<script>
export default {
  async asyncData() {
    const posts = await fetch(
      'https://api.nuxtjs.dev/planets?_embed'
    ).then((res) => res.json())

    return { posts }
  }
}
</script>