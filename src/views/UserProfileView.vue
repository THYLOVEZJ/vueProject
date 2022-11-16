<template>
  <BaseContent>
    <div class="row">
      <div class="col-3">
        <UserProfileInfo
          @follow="follow"
          @unfollow="unfollow"
          :user="user"
        ></UserProfileInfo>
        <UserProfileWrite @post_a_post="post_a_post"></UserProfileWrite>
      </div>
      <div class="col-9">
        <UserProfilePosts :posts="posts"></UserProfilePosts>
      </div>
    </div>
  </BaseContent>
</template>
  
  <script>
import BaseContent from "../components/ContentBase.vue";
import UserProfileInfo from "../components/UserProfileInfo.vue";
import UserProfilePosts from "../components/UserProfilePosts.vue";
import UserProfileWrite from "../components/UserProfileWrite.vue";
import { reactive } from "vue";

export default {
  name: "UserProfileView",
  components: {
    BaseContent,
    UserProfileInfo,
    UserProfilePosts,
    UserProfileWrite,
  },
  setup() {
    const user = reactive({
      username: "thy",
      lastName: "tang",
      firstName: "haoyu",
      id: "1",
      followerCount: 0,
      is_followed: false,
    });

    const posts = reactive({
      count: 3,
      posts: [
        {
          id: 1,
          userId: 1,
          content: "hello world",
        },
        {
          id: 2,
          userId: 2,
          content: "hi, kk",
        },
        {
          id: 3,
          userId: 3,
          content: "jj,nice to meet you",
        },
      ],
    });

    const follow = () => {
      if (user.is_followed) return;
      user.is_followed = true;
      user.followerCount++;
    };

    const unfollow = () => {
      if (!user.is_followed) return;
      user.is_followed = false;
      user.followerCount--;
    };

    const post_a_post = (content) => {
      posts.count++;
      posts.posts.unshift({
        id: posts.count,
        userId: 1,
        content: content,
      });
    };

    return {
      user,
      follow,
      unfollow,
      posts,
      post_a_post,
    };
  },
};
</script>
  
  <style scoped>
</style>
  