<template>
  <div>
    <div class="font-weight-bold" style="font-size: 16px">LIST POSTS</div>
    <br />
    <div class="row">
      <div class="card col-md-4" style="margin-bottom: 50px" v-for="post in posts" :key="post.slug">
        <NuxtLink :to="`/post/${post.slug}`">
          <img
            style="height: 300px"
            class="card-img-top"
            :src="require(`~/assets/images/${post.img}`)"
            alt="default"
          />
          <div class="card-body">
            <h5 class="card-title">{{ post.title }}</h5>
            <p class="card-text">
              {{ post.description }}
            </p>
          </div>
          <div class="card-footer">
            <small class="text-muted"
              >{{ post.author.name }} last updated {{ getMinutes(post.updatedAt) }} mins ago</small
            >
          </div>
        </NuxtLink>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    posts: Array,
    required: true,
  },
  methods: {
    getMinutes(date) {
      return new Date(date).getMinutes();
    },
  },
};
</script>