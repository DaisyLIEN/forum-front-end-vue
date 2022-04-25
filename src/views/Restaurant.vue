<template>
  <div class="container py-5">
    <!-- 餐廳資訊頁 RestaurantDetail -->
    <RestaurantDetail :initial-restaurant="restaurant" />
    <hr />
    <!-- 餐廳評論 RestaurantComments -->

    <RestaurantComments
      :restaurant-comments="restaurantComments"
      @after-delete-comment="afterDeleteComment"
    />

    <!-- 新增評論 CreateComment -->
    <CreateComment
      :restaurant-id="restaurant.id"
      @after-create-comment="afterCreateComment"
    />
  </div>
</template>

<script>
import RestaurantDetail from "./../components/RestaurantDetail.vue";
import RestaurantComments from "./../components/RestaurantComments.vue";
import CreateComment from "./../components/CreateComment.vue";

const dummyUser = {
  currentUser: {
    id: 1,
    name: "管理者",
    email: "root@example.com",
    image: "https://i.pravatar.cc/300",
    isAdmin: true,
  },
  isAuthenticated: true,
};

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
    updatedAt: "2022-04-22T06:26:24.524Z",
    CategoryId: 2,
    Category: {
      id: 2,
      name: "日本料理",
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
    },
    FavoritedUsers: [],
    LikedUsers: [],
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
  isFavorited: false,
  isLiked: false,
};

export default {
  components: {
    RestaurantDetail,
    RestaurantComments,
    CreateComment,
  },
  data() {
    return {
      restaurant: {
        id: -1, // 預期會被覆蓋，這裡只是列出資料格式，不是真的要使用這組資料
        name: "",
        categoryName: "",
        image: "",
        openingHours: "",
        tel: "",
        address: "",
        description: "",
        isFavorited: false,
        isLiked: false,
      },
      restaurantComments: [],
      currentUser: dummyUser.currentUser,
    };
  },
  created() {
    const { id: RestaurantId } = this.$route.params; // 由$route.params(vue內建方法)取得網址結構中的該頁id，並將id命名為RestaurantId
    this.fetchRestaurant(RestaurantId);
  },
  methods: {
    fetchRestaurant(restaurantId) {
      console.log("fetchRestaurant id: ", restaurantId);

      // 使用解構賦值拿出來
      const { restaurant, isFavorited, isLiked } = dummyData;
      const {
        id,
        name,
        Category, // Category.name從這裡拿
        image,
        opening_hours,
        tel,
        address,
        description,
      } = restaurant; // 再拆開

      // 把data變成想要的樣子
      this.restaurant = {
        id,
        name,
        categoryName: Category ? Category.name : "未分類",
        image,
        openingHours: opening_hours, // 用上面的名字，覆蓋
        tel,
        address,
        description,
        isFavorited,
        isLiked,
      };

      this.restaurantComments = dummyData.restaurant.Comments; // 直接取值
    },
    afterDeleteComment(commentId) {
      // 以 filter 保留未被選擇的 comment.id
      this.restaurantComments = this.restaurantComments.filter(
        (comment) => comment.id !== commentId
      );
    },
    afterCreateComment(payload) {
      const { commentId, restaurantId, text } = payload;
      this.restaurantComments.push({
        id: commentId,
        RestaurantId: restaurantId,
        User: {
          id: this.currentUser.id,
          name: this.currentUser.name,
        },
        text,
        createdAt: new Date(), // 直接抓當下的時間
      });
    },
  },
};
</script>