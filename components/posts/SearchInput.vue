<template>
  <div>
    <input
      class="form-control"
      v-model="searchQuery"
      type="search"
      autocomplete="off"
      placeholder="Search Posts title"
    />
    <ul v-if="posts.length">
      <li v-for="post of posts" :key="post.slug">
        <NuxtLink :to="`/post/${post.slug}`">
          {{ post.title }}
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchQuery: "",
      posts: [],
    };
  },
  watch: {
    async searchQuery(searchQuery) {
      if (!searchQuery) {
        this.posts = [];
        return;
      }
      
      this.posts = await this.$content("posts")
        .limit(3)
        .search('title', searchQuery)
        .fetch();
    },
  },
};
</script>

<style scoped>
.form-control {
  margin-top: 20px;
  margin-bottom: 20px;
}
</style>