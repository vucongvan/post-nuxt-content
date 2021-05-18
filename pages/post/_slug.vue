<template>
  <article>
    <nuxt-content :document="article" />
  </article>
</template>


<script>
export default {
  async asyncData({ $content, params }) {
    const article = await $content('posts', params.slug).fetch()

    const [prev, next] = await $content('posts')
      .only(['title', 'slug', 'createdAt'])
      .sortBy('createdAt', 'asc')
      .surround(params.slug)
      .fetch()
    console.log(prev, next)
    return {
      article,
      prev,
      next
    }
  },
 
  methods: {
    formatDate(date) {
      const options = { year: "numeric", month: "long", day: "numeric" };
      return new Date(date).toLocaleDateString("en", options);
    },
  },
};
</script>

<style>
.nuxt-content h2 {
  font-weight: bold;
  font-size: 28px;
}
.nuxt-content h3 {
  font-weight: bold;
  font-size: 22px;
}
.nuxt-content p {
  margin-bottom: 20px;
}
</style>