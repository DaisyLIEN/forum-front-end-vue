<template>
  <div class="container py-5">
    <NavTabs />
    <h1 class="mt-5">人氣餐廳</h1>
    <hr />
        
      <!-- UsersTopCard -->
      <RestaurantsTopCard
        v-for="restaurant in restaurants"
        :key="restaurant.id"
        :initial-restaurant="restaurant"
      />
    </div>
</template>

<script>
import NavTabs from "./../components/NavTabs.vue";
import RestaurantsTopCard from "./../components/RestaurantsTopCard.vue";

const dummyData = {
  restaurants: [
    {
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
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 49,
      name: "Rubye Crooks I",
      tel: "681-534-8283",
      address: "052 John Forge",
      opening_hours: "08:00",
      description: "Impedit tenetur et enim est.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=91.52651048066664",
      viewCounts: 0,
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
      CategoryId: 4,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 48,
      name: "Ryleigh Mayert",
      tel: "888.560.3609 x7263",
      address: "2765 Mertz Village",
      opening_hours: "08:00",
      description: "Perferendis voluptatem veniam ea doloremque praese",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=59.84883212734806",
      viewCounts: 0,
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
      CategoryId: 2,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 47,
      name: "Millie Gutmann",
      tel: "(536) 155-5123",
      address: "1991 Kirlin Cape",
      opening_hours: "08:00",
      description: "Quam similique velit laborum rerum. In hic earum s",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=26.90935612885812",
      viewCounts: 0,
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
      CategoryId: 2,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 46,
      name: "Ayden Kertzmann",
      tel: "762.845.6832 x5004",
      address: "676 Deanna Shores",
      opening_hours: "08:00",
      description: "laudantium",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=42.230061536964755",
      viewCounts: 0,
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
      CategoryId: 2,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 45,
      name: "Georgette Pagac",
      tel: "1-777-141-9492 x69879",
      address: "4440 Kutch Pike",
      opening_hours: "08:00",
      description: "ab qui ut",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=4.070923513608626",
      viewCounts: 0,
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
      CategoryId: 2,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 44,
      name: "Kareem Howell",
      tel: "(612) 163-5365 x0696",
      address: "33177 Muller Pines",
      opening_hours: "08:00",
      description: "Autem non illum est esse animi nihil.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=20.749963832656416",
      viewCounts: 0,
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
      CategoryId: 5,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 43,
      name: "Lisa Hickle",
      tel: "429-208-1701",
      address: "232 Pfeffer Forges",
      opening_hours: "08:00",
      description: "Earum odio mollitia in ipsam. Ipsa neque delectus ",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=16.47603494495453",
      viewCounts: 0,
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
      CategoryId: 2,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 42,
      name: "Joseph Koss",
      tel: "457-960-4622",
      address: "838 Kaley Lights",
      opening_hours: "08:00",
      description: "Ipsam quaerat quasi quae ea quisquam possimus ut d",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=50.459603518456795",
      viewCounts: 0,
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
      CategoryId: 2,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 41,
      name: "Miss Freda Dare",
      tel: "1-724-745-0101 x50404",
      address: "109 Nona Fort",
      opening_hours: "08:00",
      description: "Veniam quos nemo qui.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=68.62235863225965",
      viewCounts: 0,
      createdAt: "2022-04-20T08:03:19.000Z",
      updatedAt: "2022-04-20T08:03:19.000Z",
      CategoryId: 3,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
  ],
};

export default {
  components: {
    NavTabs,
    RestaurantsTopCard,
  },
  data() {
    return {
      restaurants: [] // 注意是陣列
    };
  },
  created() {
    this.fetchRestaurant();
  },
  methods: {
    fetchRestaurant() {
      this.restaurants = dummyData.restaurants
    },
  },
};
</script>