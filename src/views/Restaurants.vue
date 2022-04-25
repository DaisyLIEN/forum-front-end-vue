<template>
  <div class="container py-5">
    <NavTabs />
    <!-- RestaurantsNavPills -->
    <RestaurantsNavPills :categories="categories" />

    <div class="row">
      <!-- RestaurantCard -->
      <!-- kebab-case in HTML (initial-restaurant) -->
      <RestaurantCard
        v-for="restaurant in restaurants"
        :key="restaurant.id"
        :initial-restaurant="restaurant"
      />
    </div>

    <!-- RestaurantPagination -->
    <RestaurantsPagination
      v-if="totalPage.length > 1"
      :category-id="categoryId"
      :current-page="currentPage"
      :total-page="totalPage"
      :previous-page="previousPage"
      :next-page="nextPage"
    />
  </div>
</template>

<script>
import NavTabs from "./../components/NavTabs";
import RestaurantCard from "./../components/RestaurantCard";
import RestaurantsNavPills from "./../components/RestaurantsNavPills";
import RestaurantsPagination from "./../components/RestaurantsPagination";

// 模擬API
const dummyData = {
  restaurants: [
    {
      id: 1,
      name: "Thora Wehner",
      tel: "562.618.0600 x32493",
      address: "05155 Carol Glens",
      opening_hours: "08:00",
      description: "Eaque inventore cupiditate aut architecto voluptat",
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
      isFavorited: false,
      isLiked: false,
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
      isFavorited: false,
      isLiked: false,
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
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 4,
      name: "Zola Mayer",
      tel: "1-788-902-6782 x3864",
      address: "04235 Morar Extensions",
      opening_hours: "08:00",
      description: "Aspernatur aperiam excepturi consequatur cupiditat",
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
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 5,
      name: "Gregg Lueilwitz",
      tel: "179.510.3636 x499",
      address: "7866 Verla Center",
      opening_hours: "08:00",
      description: "Et reprehenderit doloremque vitae quidem impedit a",
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
      isFavorited: false,
      isLiked: false,
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
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 7,
      name: "Dr. Yasmin Rogahn",
      tel: "1-038-789-4125 x912",
      address: "20663 Austin Crest",
      opening_hours: "08:00",
      description: "Est tenetur ratione nulla et quia molestiae. In re",
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
      isFavorited: false,
      isLiked: false,
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
      isFavorited: false,
      isLiked: false,
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
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 10,
      name: "Miss Nash Abshire",
      tel: "132-834-5849 x26613",
      address: "16761 Shemar Canyon",
      opening_hours: "08:00",
      description: "Corporis consequatur perspiciatis aut commodi volu",
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
      isFavorited: false,
      isLiked: false,
    },
  ],
  categories: [
    {
      id: 1,
      name: "中式料理",
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
    },
    {
      id: 2,
      name: "日本料理",
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
    },
    {
      id: 3,
      name: "義大利料理",
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
    },
    {
      id: 4,
      name: "墨西哥料理",
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
    },
    {
      id: 5,
      name: "素食料理",
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
    },
    {
      id: 6,
      name: "美式料理",
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
    },
    {
      id: 7,
      name: "複合式料理",
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
    },
  ],
  categoryId: "",
  page: 1,
  totalPage: [1, 2, 3, 4, 5],
  prev: 1,
  next: 2,
};

export default {
  components: {
    NavTabs,
    RestaurantCard,
    RestaurantsNavPills,
    RestaurantsPagination,
  },
  data() {
    return {
      restaurants: [],
      categories: [],
      categoryId: -1, // 當下用哪個類別來篩選餐廳
      currentPage: 1,
      totalPage: [], // -1
      previousPage: -1,
      nextPage: -1,
    };
  },
  created() {
    this.fetchRestaurants();
  },
  methods: {
    fetchRestaurants() {
      const {
        restaurants,
        categories,
        categoryId,
        page,
        totalPage,
        prev,
        next,
      } = dummyData;
      this.restaurants = restaurants;
      this.categories = categories;
      this.categoryId = categoryId;
      this.currentPage = page;
      this.totalPage = totalPage;
      this.previousPage = prev;
      this.nextPage = next;
    },
  },
};
</script>