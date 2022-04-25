<template>
  <div class="container py-5">
    <NavTabs />

    <h1 class="mt-5">最新動態</h1>
    <hr />
    <div class="row">
      <div class="col-md-6">
        <h3>最新餐廳</h3>
        <!-- 最新餐廳 NewestRestaurants -->
        <!-- Prop :restaurants(自訂)="restaurants(下方data)"-->
        <NewestRestaurants :restaurants="restaurants" />
      </div>
      <div class="col-md-6">
        <h3>最新評論</h3>
        <!-- 最新評論 NewestComments-->
        <NewestComments :comments="comments" />        
      </div>
    </div>
  </div>
</template>

<script>
import NavTabs from "./../components/NavTabs.vue";
import NewestRestaurants from "./../components/NewestRestaurants.vue";
import NewestComments from './../components/NewestComments.vue'

// 模擬從API請求來的資料
const dummyData = {
  restaurants: [
    {
      id: 1,
      name: "Thora Wehner",
      tel: "562.618.0600 x32493",
      address: "05155 Carol Glens",
      opening_hours: "08:00",
      description:
        "Eaque inventore cupiditate aut architecto voluptatem vel voluptatem. Mollitia qui quia necessitatibus esse asperiores et sed aspernatur sed. Illum incidunt optio veniam quo id omnis. Aut aut impedit cumque fuga. Et ut id velit impedit.\n \rVeniam est debitis mollitia. Minus est soluta sit sequi possimus dolorem culpa. Voluptas vero aut nisi. Veritatis natus perspiciatis et molestiae quod quod. Quia quo facilis fuga autem dolorum ut. Et at officia.\n \rSint quis modi repellendus. Vitae perferendis aliquam. Blanditiis reiciendis tempore voluptatem minima hic possimus rem consectetur.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=36.86018998308689",
      viewCounts: 0,
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-04-20T08:03:19.000Z",
        updatedAt: "2022-04-20T08:03:19.000Z",
      },
    },
    {
      id: 2,
      name: "Serena Daniel II",
      tel: "186.348.5064 x07325",
      address: "3048 Brielle Court",
      opening_hours: "08:00",
      description: "enim et expedita",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=22.603930826896846",
      viewCounts: 0,
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2022-04-20T08:03:19.000Z",
        updatedAt: "2022-04-20T08:03:19.000Z",
      },
    },
    {
      id: 3,
      name: "Kamille Weimann",
      tel: "251.074.4517 x35123",
      address: "95020 Vivian Corner",
      opening_hours: "08:00",
      description: "animi",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=97.9559912206374",
      viewCounts: 0,
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-04-20T08:03:19.000Z",
        updatedAt: "2022-04-20T08:03:19.000Z",
      },
    },
    {
      id: 4,
      name: "Zola Mayer",
      tel: "1-788-902-6782 x3864",
      address: "04235 Morar Extensions",
      opening_hours: "08:00",
      description:
        "Aspernatur aperiam excepturi consequatur cupiditate perferendis tempora.\nSaepe corrupti illo sunt et dolorem vel.\nVeniam at ut voluptatem saepe corporis non sint porro consequatur.\nSit nam est ut.\nUt sint qui voluptas est ut enim quis et nihil.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=50.95132556881272",
      viewCounts: 0,
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-04-20T08:03:19.000Z",
        updatedAt: "2022-04-20T08:03:19.000Z",
      },
    },
    {
      id: 5,
      name: "Gregg Lueilwitz",
      tel: "179.510.3636 x499",
      address: "7866 Verla Center",
      opening_hours: "08:00",
      description:
        "Et reprehenderit doloremque vitae quidem impedit assumenda modi. Ut eos labore sed velit excepturi aperiam. Aut quas est cumque tempore libero quo iusto et. Quibusdam fugit cum expedita iusto amet facere consequatur fugit. Aperiam temporibus repellat eaque rerum unde rerum.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=98.31169946287572",
      viewCounts: 0,
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
      CategoryId: 1,
      Category: {
        id: 1,
        name: "中式料理",
        createdAt: "2022-04-20T08:03:19.000Z",
        updatedAt: "2022-04-20T08:03:19.000Z",
      },
    },
    {
      id: 6,
      name: "Horace Abshire",
      tel: "1-296-786-1584 x165",
      address: "213 Mozelle Ville",
      opening_hours: "08:00",
      description: "sit",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=72.47145485418717",
      viewCounts: 0,
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-04-20T08:03:19.000Z",
        updatedAt: "2022-04-20T08:03:19.000Z",
      },
    },
    {
      id: 7,
      name: "Dr. Yasmin Rogahn",
      tel: "1-038-789-4125 x912",
      address: "20663 Austin Crest",
      opening_hours: "08:00",
      description:
        "Est tenetur ratione nulla et quia molestiae. In reiciendis in omnis. Quos dolore sed sed numquam aut est est sapiente eos. Distinctio omnis pariatur quis voluptatum qui quo aperiam qui doloribus. Mollitia totam repellendus aut totam dolores dicta voluptatem. Provident quo suscipit molestiae tenetur ab.\n \rDebitis facere animi voluptates voluptatum suscipit vitae. Sint dicta explicabo labore. Voluptates sed quos quia quidem minus tenetur. Odit fugiat sed non animi ab minima. Eius itaque aperiam dolor laborum. Sint et enim iure autem et doloribus enim non inventore.\n \rAutem rerum porro quo officia id molestiae aut voluptas. Ab esse provident inventore consequatur sed. Ipsa dicta sapiente corrupti sit.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=0.9377455859799433",
      viewCounts: 0,
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-04-20T08:03:19.000Z",
        updatedAt: "2022-04-20T08:03:19.000Z",
      },
    },
    {
      id: 8,
      name: "Maria Hamill I",
      tel: "213-122-1839 x1196",
      address: "16060 Casper Meadow",
      opening_hours: "08:00",
      description: "At eius sed sunt et nisi rerum perspiciatis.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=60.48930631450402",
      viewCounts: 0,
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-04-20T08:03:19.000Z",
        updatedAt: "2022-04-20T08:03:19.000Z",
      },
    },
    {
      id: 9,
      name: "Weston Stiedemann",
      tel: "1-730-961-2218 x4886",
      address: "447 Talon Roads",
      opening_hours: "08:00",
      description: "Dolores eos nisi rerum.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=30.58032128554311",
      viewCounts: 0,
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-04-20T08:03:19.000Z",
        updatedAt: "2022-04-20T08:03:19.000Z",
      },
    },
    {
      id: 10,
      name: "Miss Nash Abshire",
      tel: "132-834-5849 x26613",
      address: "16761 Shemar Canyon",
      opening_hours: "08:00",
      description:
        "Corporis consequatur perspiciatis aut commodi voluptate. Qui temporibus earum voluptatem reprehenderit est consequatur ut qui. Quia nihil eveniet veniam eos veniam.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=97.64755859057317",
      viewCounts: 0,
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-04-20T08:03:19.000Z",
        updatedAt: "2022-04-20T08:03:19.000Z",
      },
    },
  ],
  comments: [
    {
      id: 4,
      text: "Sunt odit nesciunt numquam et.",
      UserId: 1,
      RestaurantId: 4,
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
      Restaurant: {
        id: 4,
        name: "Zola Mayer",
        tel: "1-788-902-6782 x3864",
        address: "04235 Morar Extensions",
        opening_hours: "08:00",
        description:
          "Aspernatur aperiam excepturi consequatur cupiditate perferendis tempora.\nSaepe corrupti illo sunt et dolorem vel.\nVeniam at ut voluptatem saepe corporis non sint porro consequatur.\nSit nam est ut.\nUt sint qui voluptas est ut enim quis et nihil.",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=50.95132556881272",
        viewCounts: 0,
        createdAt: "2022-04-20T08:03:19.000Z",
        updatedAt: "2022-04-20T08:03:19.000Z",
        CategoryId: 3,
      },
    },
    {
      id: 23,
      text: "Asperiores nesciunt consequatur amet repellendus rerum deleniti reprehenderit.",
      UserId: 1,
      RestaurantId: 23,
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
      Restaurant: {
        id: 23,
        name: "Sydnie Davis",
        tel: "1-851-944-9670 x1663",
        address: "04100 Labadie Freeway",
        opening_hours: "08:00",
        description:
          "Facilis magnam soluta possimus et dolorem nihil ad quidem.\nAb et non est aliquid consectetur.",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=37.25749312149604",
        viewCounts: 0,
        createdAt: "2022-04-20T08:03:19.000Z",
        updatedAt: "2022-04-20T08:03:19.000Z",
        CategoryId: 4,
      },
    },
    {
      id: 38,
      text: "Omnis recusandae est et totam consectetur sint pariatur.",
      UserId: 1,
      RestaurantId: 38,
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
      Restaurant: {
        id: 38,
        name: "Juliana McDermott",
        tel: "388-376-7534 x29424",
        address: "67692 Elroy Shore",
        opening_hours: "08:00",
        description:
          "Vel totam quia et exercitationem eum ut aperiam voluptatem. Aut molestiae eum quisquam tempora nemo libero. Eos nemo perferendis.\n \rConsequuntur adipisci earum. Non non ducimus et est nulla et enim sunt animi. Qui dicta ab debitis consequatur doloremque facere sunt nesciunt nisi. Amet quos doloribus quia non et blanditiis pariatur.\n \rSimilique provident optio nesciunt non. Voluptates quas nam voluptatem autem porro est aperiam. Quisquam ut facere excepturi. Id autem sed consectetur eos deleniti eos.",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=52.31866450809937",
        viewCounts: 0,
        createdAt: "2022-04-20T08:03:19.000Z",
        updatedAt: "2022-04-20T08:03:19.000Z",
        CategoryId: 2,
      },
    },
    {
      id: 60,
      text: "Occaecati eos eos quasi necessitatibus et voluptates ut.",
      UserId: 1,
      RestaurantId: 10,
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
      Restaurant: {
        id: 10,
        name: "Miss Nash Abshire",
        tel: "132-834-5849 x26613",
        address: "16761 Shemar Canyon",
        opening_hours: "08:00",
        description:
          "Corporis consequatur perspiciatis aut commodi voluptate. Qui temporibus earum voluptatem reprehenderit est consequatur ut qui. Quia nihil eveniet veniam eos veniam.",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=97.64755859057317",
        viewCounts: 0,
        createdAt: "2022-04-20T08:03:19.000Z",
        updatedAt: "2022-04-20T08:03:19.000Z",
        CategoryId: 3,
      },
    },
    {
      id: 83,
      text: "Est velit aut suscipit provident soluta ut voluptas.",
      UserId: 1,
      RestaurantId: 33,
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
      Restaurant: {
        id: 33,
        name: "Mrs. Daron Anderson",
        tel: "1-089-446-4083 x01092",
        address: "59771 Reinger Haven",
        opening_hours: "08:00",
        description: "qui laudantium expedita",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=14.542998623940617",
        viewCounts: 0,
        createdAt: "2022-04-20T08:03:19.000Z",
        updatedAt: "2022-04-20T08:03:19.000Z",
        CategoryId: 1,
      },
    },
    {
      id: 108,
      text: "Expedita soluta aperiam esse libero minus qui cumque non tenetur.",
      UserId: 1,
      RestaurantId: 8,
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
      Restaurant: {
        id: 8,
        name: "Maria Hamill I",
        tel: "213-122-1839 x1196",
        address: "16060 Casper Meadow",
        opening_hours: "08:00",
        description: "At eius sed sunt et nisi rerum perspiciatis.",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=60.48930631450402",
        viewCounts: 0,
        createdAt: "2022-04-20T08:03:19.000Z",
        updatedAt: "2022-04-20T08:03:19.000Z",
        CategoryId: 3,
      },
    },
    {
      id: 2,
      text: "Et qui ut laboriosam asperiores suscipit natus eum corporis ea.",
      UserId: 2,
      RestaurantId: 2,
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
      User: {
        id: 2,
        name: "user1",
        email: "user1@example.com",
        password:
          "$2a$10$0Wf5sWQj5keMaMD8q970a.XqwKdxPS.WbXVHPxEqZV52.0RiFv4Ne",
        isAdmin: false,
        image: null,
        createdAt: "2022-04-20T08:03:18.000Z",
        updatedAt: "2022-04-20T08:03:18.000Z",
      },
      Restaurant: {
        id: 2,
        name: "Serena Daniel II",
        tel: "186.348.5064 x07325",
        address: "3048 Brielle Court",
        opening_hours: "08:00",
        description: "enim et expedita",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=22.603930826896846",
        viewCounts: 0,
        createdAt: "2022-04-20T08:03:19.000Z",
        updatedAt: "2022-04-20T08:03:19.000Z",
        CategoryId: 5,
      },
    },
    {
      id: 28,
      text: "Itaque doloremque qui laborum est.",
      UserId: 2,
      RestaurantId: 28,
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
      User: {
        id: 2,
        name: "user1",
        email: "user1@example.com",
        password:
          "$2a$10$0Wf5sWQj5keMaMD8q970a.XqwKdxPS.WbXVHPxEqZV52.0RiFv4Ne",
        isAdmin: false,
        image: null,
        createdAt: "2022-04-20T08:03:18.000Z",
        updatedAt: "2022-04-20T08:03:18.000Z",
      },
      Restaurant: {
        id: 28,
        name: "Bianka Murray DDS",
        tel: "(821) 073-9970",
        address: "29532 Donnell Villages",
        opening_hours: "08:00",
        description: "Et unde sit.",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=75.78155544932766",
        viewCounts: 0,
        createdAt: "2022-04-20T08:03:19.000Z",
        updatedAt: "2022-04-20T08:03:19.000Z",
        CategoryId: 4,
      },
    },
    {
      id: 73,
      text: "Est beatae sed.",
      UserId: 2,
      RestaurantId: 23,
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
      User: {
        id: 2,
        name: "user1",
        email: "user1@example.com",
        password:
          "$2a$10$0Wf5sWQj5keMaMD8q970a.XqwKdxPS.WbXVHPxEqZV52.0RiFv4Ne",
        isAdmin: false,
        image: null,
        createdAt: "2022-04-20T08:03:18.000Z",
        updatedAt: "2022-04-20T08:03:18.000Z",
      },
      Restaurant: {
        id: 23,
        name: "Sydnie Davis",
        tel: "1-851-944-9670 x1663",
        address: "04100 Labadie Freeway",
        opening_hours: "08:00",
        description:
          "Facilis magnam soluta possimus et dolorem nihil ad quidem.\nAb et non est aliquid consectetur.",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=37.25749312149604",
        viewCounts: 0,
        createdAt: "2022-04-20T08:03:19.000Z",
        updatedAt: "2022-04-20T08:03:19.000Z",
        CategoryId: 4,
      },
    },
    {
      id: 100,
      text: "Velit quam autem error sed sapiente deserunt quia repellat.",
      UserId: 2,
      RestaurantId: 50,
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
      User: {
        id: 2,
        name: "user1",
        email: "user1@example.com",
        password:
          "$2a$10$0Wf5sWQj5keMaMD8q970a.XqwKdxPS.WbXVHPxEqZV52.0RiFv4Ne",
        isAdmin: false,
        image: null,
        createdAt: "2022-04-20T08:03:18.000Z",
        updatedAt: "2022-04-20T08:03:18.000Z",
      },
      Restaurant: {
        id: 50,
        name: "Alyson Crona",
        tel: "623-378-6265 x648",
        address: "5451 Murl Cove",
        opening_hours: "08:00",
        description: "eos officiis itaque",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=46.24284915815979",
        viewCounts: 0,
        createdAt: "2022-04-20T08:03:19.000Z",
        updatedAt: "2022-04-20T08:03:19.000Z",
        CategoryId: 4,
      },
    },
  ],
};

export default {
  components: {
    NavTabs,
    NewestRestaurants,
    NewestComments
  },
  data () {
    return {
      restaurants: [],
      comments: []
    }
  },
  created () {
    this.fetchFeeds()
  },
  methods: {
    fetchFeeds () {
      this.restaurants = dummyData.restaurants
      this.comments = dummyData.comments
    }
  }
};
</script>    