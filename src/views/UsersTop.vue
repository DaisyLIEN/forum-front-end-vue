<template>
  <div class="container py-5">
    <NavTabs />
    <h1 class="mt-5">美食達人</h1>
    <hr />
    <div class="row text-center">
    <UsersTopCard v-for="user in users" :key="user.id" :initial-user="user" />
    </div>
  </div>
</template>

<script>
import NavTabs from "./../components/NavTabs";
import UsersTopCard from "./../components/UsersTopCard";

// 模擬API假資料
const dummyData = {
  users: [
    {
      id: 1,
      name: "root",
      email: "root@example.com",
      password: "$2a$10$wRpTyTQ5yTLDiJDW0qESWeH8jPXVHmk4thK.Zk/l06kt9zM93DXZe",
      isAdmin: true,
      image: null,
      createdAt: "2022-04-20T08:03:18.000Z",
      updatedAt: "2022-04-20T08:03:18.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false,
    },
    {
      id: 2,
      name: "user1",
      email: "user1@example.com",
      password: "$2a$10$0Wf5sWQj5keMaMD8q970a.XqwKdxPS.WbXVHPxEqZV52.0RiFv4Ne",
      isAdmin: false,
      image: null,
      createdAt: "2022-04-20T08:03:18.000Z",
      updatedAt: "2022-04-20T08:03:18.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false,
    },
    {
      id: 3,
      name: "user2",
      email: "user2@example.com",
      password: "$2a$10$kvs5K1ahKZQfquE7qA6A.e.z1ldSamari7b3VrI2jzbVVVQmnIPea",
      isAdmin: false,
      image: null,
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false,
    },
  ],
};

export default {
  components: {
    NavTabs,
    UsersTopCard
  },
  data () {
    return {
      users: []
    }
  },
  created () {
    this.fetchUsersTop()
  },
  methods: {
    fetchUsersTop () {
      this.users = dummyData.users
    }
  }  
};
</script>