<template>
  <div class="card">
    <div class="card-body">
      <div class="row">
        <div class="col-3">
          <img
            class="img-fluid"
            src="https://cdn.acwing.com/media/user/profile/photo/78772_lg_a08174967e.jpg"
            alt=""
          />
        </div>
        <div class="col-9">
          <div class="username">{{ fullname }}</div>
          <div class="fans">粉丝数： {{ user.followerCount }}</div>
          <button
            type="button"
            @click="follow"
            v-if="!user.is_followed"
            class="btn btn-secondary btn-sm"
          >
            +关注
          </button>
          <button
            type="button"
            @click="unfollow"
            v-if="user.is_followed"
            class="btn btn-secondary btn-sm"
          >
            取消关注
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { computed } from "vue";
export default {
  name: "UserProfileInfo",
  props: {
    user: {
      type: Object,
      required: true,
    },
  },
  setup(props, context) {
    let fullname = computed(
      () => props.user.lastname + " " + props.user.firstname
    );
    const follow = () => {
      context.emit('follow');
    };
    const unfollow = () => {
      context.emit("unfollow");
    };

    return {
      fullname,
      follow,
      unfollow,
    };
  },
};
</script>
<style scoped>
img {
  border-radius: 50%;
}
.username {
  font-weight: bold;
}
.fans {
  font-size: 12px;
  color: gray;
}
button {
  padding: 2px 4px;
  font-size: 12px;
}
</style>