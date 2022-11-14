<template>
  <div class="card">
    <div class="card-body">
      <div v-for="post in posts.posts" :key="post.id">
        <div class="card single-posts">
          <div class="card-body">
            {{ post.content }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "UserProfilePosts",
  props: {
    posts: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style>
.single-posts {
  margin-bottom: 10px;
}
</style>