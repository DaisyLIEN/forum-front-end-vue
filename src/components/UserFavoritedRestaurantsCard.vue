<template>
  <div class="card">
    <div class="card-header"><strong>{{ favoritedRestaurantsCounts }}</strong> 收藏的餐廳</div>
    <div class="card-body">
      <router-link v-for="favoritedRestaurant in favoritedRestaurants" :key="favoritedRestaurant.id" :to="{ name: 'restaurant', params: { id: favoritedRestaurant.id }}">
        <img
          :src="favoritedRestaurant.image"
          width="60"
          height="60"
          class="avatar"
        />
      </router-link> 
    </div>
  </div>
</template>

<script>
export default {
  props: {
    initialFavoritedRestaurants: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      favoritedRestaurants: this.initialFavoritedRestaurants,
      favoritedRestaurantsCounts: this.initialFavoritedRestaurants.length
    };
  },
};
</script>