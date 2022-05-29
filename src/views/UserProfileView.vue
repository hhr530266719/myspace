<template>
  <ContentBase>
    <div class="row">
      <div class="col-3">
        <UserProfileInfo @follow = "follow" @unfollow = "unfollow" :user="user"></UserProfileInfo>
      </div>
      <dic class="col-9">
        <UserProfilePosts></UserProfilePosts>
      </dic>
    </div>
  </ContentBase>
</template>

<script>
import ContentBase from "../components/ContentBase.vue";
import { reactive } from "vue";
import UserProfileInfo from "../components/UserProfileInfo.vue";
import UserProfilePosts from "../components/UserProfilePosts.vue";

export default {
  name: "UserProfileView",
  components: {
    ContentBase,
    UserProfileInfo,
    UserProfilePosts,
  },
  setup() {
    const user = reactive({
      username: "hanhuarong",
      lastname: "韩 ",
      firstname: "华荣",
      followerCount: 0,
      is_followed: false,
    });
    const follow = () => {
      if (user.is_followed) return;
      user.is_followed = true;
      user.followerCount ++;
       

    };
    const unfollow = () =>{
      if (!user.is_followed)  return ;
      user.is_followed = false;
      user.followerCount --; 

    }
    return {
      user,
      follow,
      unfollow,
    };
  },
};
</script>
<style scoped>
</style>
