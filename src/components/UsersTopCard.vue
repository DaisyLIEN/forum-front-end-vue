<template>  
    <div class="col-3">
      <router-link :to="{ name: 'user', params: { id: user.id }}">
        <img
          :src="user.image? user.image : 'https://i.pravatar.cc/300'"
          width="60"
          height="60"
          class="avatar"
        />
      </router-link>      
      <h2>{{ user.name }}</h2>
      <span class="badge badge-secondary"
        >追蹤人數：{{ user.FollowerCount }}</span
      >
      <p class="mt-3">
        <button
          v-if="user.isFollowed"
          @click.prevent.stop="deleteFollow"
          type="button"
          class="btn btn-danger"
        >
          取消追蹤
        </button>
        <button
          v-else
          @click.prevent.stop="addFollow"
          type="button"
          class="btn btn-primary"
        >
          追蹤
        </button>
      </p>
    </div>
</template>

<script>
export default {
  props: {
    initialUser: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      user: this.initialUser, // 自行copy，以便修改data
    };
  },
  methods: {
    addFollow() {
      this.user = {
        ...this.user,
        isFollowed: true,
      };
    },
    deleteFollow() {
      this.user = {
        ...this.user,
        isFollowed: false,
      };
    },
  },
};
</script>