<template>
  <BaseContent>
    <div class="card" v-for="user in users" :key="user.id">
      <div class="card-body">
        <div class="row">
          <div class="col-1">
            <img class="img-fluid" :src="user.photo" alt="" />
          </div>
          <div class="col-11">
            <div class="username">{{ user.username }}</div>
            <div class="follower-count">{{ user.followerCount }}</div>
          </div>
        </div>
      </div>
    </div>
  </BaseContent>
</template>
  
<script>
import BaseContent from "../components/ContentBase.vue";
import $ from "jquery";
import { ref } from "vue";
export default {
  name: "UserListView",
  components: {
    BaseContent,
  },
  setup() {
    let users = ref([]);

    $.ajax({
      url: "https://app165.acapp.acwing.com.cn/myspace/userlist/",
      type: "get",
      success(resp) {
        console.log(resp);
        users.value = resp;
      },
    });

    return {
      users,
    };
  },
};
</script>
  
<style scoped>
img {
  border-radius: 50%;
}
.username {
  font-weight: bolder;
  height: 50%;
}
.follower-count {
  font-size: 12px;
  color: grey;
  height: 50%;
}
.card {
  margin-bottom: 20px;
  cursor: pointer;
}
.card:hover {
  box-shadow: 10px 5px 5px lightgray;
  transition: 500ms;
}
</style>
  