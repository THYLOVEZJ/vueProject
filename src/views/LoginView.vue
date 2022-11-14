<template>
  <BaseContent>
    <form>
      <div class="mb-3">
        <label for="username" class="form-label">用户名</label>
        <input
          v-model="username"
          type="text"
          class="form-control"
          id="username"
        />
      </div>
      <div class="mb-3">
        <label for="password" class="form-label">密码</label>
        <input
          v-model="password"
          type="password"
          class="form-control"
          id="password"
        />
      </div>
      <button type="submit" class="btn btn-primary">Submit</button>
    </form>
  </BaseContent>
</template>
  
  <script>
import BaseContent from "../components/ContentBase.vue";
import { ref } from "vue";
export default {
  name: "LoginView",
  components: {
    BaseContent,
  },
  setup() {
    let username = ref("");
    let password = ref("");
    return {
      username,
      password,
    };
  },
};
</script>
  
<style>
</style>
  