<template>
  <div class="container">
    <Search-Input />
    <List-Post :posts="posts"/>
  </div>
</template>

<script>
import ListPost from '@/components/posts/ListPost'
import SearchInput from '@/components/posts/SearchInput'

export default {
  components: {
    ListPost,
    SearchInput
  },
  async asyncData({ $content, params }) {
    const posts = await $content("posts", params.slug)
      .only(["title", "description", "img", "slug", "author", "updatedAt"])
      .sortBy("createdAt", "desc")
      .fetch();
    return {
      posts,
    };
  },
  methods: {
    
  }
};
</script>

<style>
</style>
