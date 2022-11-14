<template>
  <div class="card edit-field">
    <div class="card-body">
      <label for="edit-posts" class="form-label">发帖</label>
      <textarea
        v-model="content"
        class="form-control"
        id="edit-posts"
        rows="3"
      ></textarea>
      <button type="button" @click="post_a_post" class="btn btn-primary btn-sm">
        发帖
      </button>
    </div>
  </div>
</template>

<script>
import { ref } from "@vue/reactivity";
export default {
  name: "UserProfileWrite",
  setup(props, context) {
    let content = ref("");

    const post_a_post = () => {
      context.emit("post_a_post", content.value);
      content.value = "";
    };

    return {
      content,
      post_a_post,
    };
  },
};
</script>


<style scoped>
.edit-field {
  margin-top: 10px;
}

button {
  margin-top: 10px;
}
</style>