<template>
  <div class="container py-5">
    <div>
      <h1>{{ restaurant.name }}</h1>
      <span class="badge badge-secondary mt-1 mb-3">
        {{ restaurant.categoryName }}
      </span>
    </div>

    <hr />

    <ul>
      <li>評論數： {{ restaurant.commentsLength }}</li>
      <li>瀏覽次數： {{ restaurant.viewCounts }}</li>
    </ul>

    <button type="button" class="btn btn-link" @click="$router.back()">
      回上一頁
    </button>
  </div>
</template>

<script>
const dummyData = {
  restaurant: {
    id: 1,
    name: "Thora Wehner",
    tel: "562.618.0600 x32493",
    address: "05155 Carol Glens",
    opening_hours: "08:00",
    description:
      "Eaque inventore cupiditate aut architecto voluptatem vel voluptatem. Mollitia qui quia necessitatibus esse asperiores et sed aspernatur sed. Illum incidunt optio veniam quo id omnis. Aut aut impedit cumque fuga. Et ut id velit impedit.\n \rVeniam est debitis mollitia. Minus est soluta sit sequi possimus dolorem culpa. Voluptas vero aut nisi. Veritatis natus perspiciatis et molestiae quod quod. Quia quo facilis fuga autem dolorum ut. Et at officia.\n \rSint quis modi repellendus. Vitae perferendis aliquam. Blanditiis reiciendis tempore voluptatem minima hic possimus rem consectetur.",
    image:
      "https://loremflickr.com/320/240/restaurant,food/?random=36.86018998308689",
    viewCounts: 1,
    createdAt: "2022-04-20T08:03:19.000Z",
    updatedAt: "2022-04-22T06:26:24.000Z",
    CategoryId: 2,
    Category: {
      id: 2,
      name: "日本料理",
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
    },
    Comments: [
      {
        id: 1,
        text: "Sapiente ut repellat sapiente nobis facere et modi soluta.",
        UserId: 1,
        RestaurantId: 1,
        createdAt: "2022-04-20T08:03:19.000Z",
        updatedAt: "2022-04-20T08:03:19.000Z",
        User: {
          id: 1,
          name: "root",
          email: "root@example.com",
          password:
            "$2a$10$wRpTyTQ5yTLDiJDW0qESWeH8jPXVHmk4thK.Zk/l06kt9zM93DXZe",
          isAdmin: true,
          image: null,
          createdAt: "2022-04-20T08:03:18.000Z",
          updatedAt: "2022-04-20T08:03:18.000Z",
        },
      },
      {
        id: 51,
        text: "Occaecati consequatur sit voluptatibus nihil ipsa laboriosam amet aliquam.",
        UserId: 1,
        RestaurantId: 1,
        createdAt: "2022-04-20T08:03:19.000Z",
        updatedAt: "2022-04-20T08:03:19.000Z",
        User: {
          id: 1,
          name: "root",
          email: "root@example.com",
          password:
            "$2a$10$wRpTyTQ5yTLDiJDW0qESWeH8jPXVHmk4thK.Zk/l06kt9zM93DXZe",
          isAdmin: true,
          image: null,
          createdAt: "2022-04-20T08:03:18.000Z",
          updatedAt: "2022-04-20T08:03:18.000Z",
        },
      },
      {
        id: 101,
        text: "Dolores esse dolores.",
        UserId: 3,
        RestaurantId: 1,
        createdAt: "2022-04-20T08:03:19.000Z",
        updatedAt: "2022-04-20T08:03:19.000Z",
        User: {
          id: 3,
          name: "user2",
          email: "user2@example.com",
          password:
            "$2a$10$kvs5K1ahKZQfquE7qA6A.e.z1ldSamari7b3VrI2jzbVVVQmnIPea",
          isAdmin: false,
          image: null,
          createdAt: "2022-04-20T08:03:19.000Z",
          updatedAt: "2022-04-20T08:03:19.000Z",
        },
      },
    ],
  },
};

export default {
  data() {
    return {
      restaurant: {
        id: -1,
        name: '',
        categoryName: '',
        viewCounts: 0,
        commentsLength: 0
      }
    }
  },
  created() {
    // const { id: restaurantId } = this.$route.params
    this.fetchRestaurant()
  },
  methods: {
    fetchRestaurant() {
      const { id, name, Category, viewCounts, Comments } = dummyData.restaurant
      this.restaurant = {
        id,
        name,
        categoryName: Category ? Category.name : '未分類',
        viewCounts,
        commentsLength: Comments.length
      }
    }
  }
};
</script>