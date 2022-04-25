<template>
  <div class="card">
    <div class="card-header">
      最新餐廳
    </div>
    <div class="card-body">
      <div v-for="restaurant in restaurants" :key="restaurant.id">

        <h4>
          <router-link
      :to="{ name: 'restaurant', params: {id: restaurant.id}}"
    >
      {{ restaurant.name }}
    </router-link>
          <small>{{ restaurant.Category ? restaurant.Category.name : '未分類' }}</small>
        </h4>
        <p>{{ restaurant.description }}</p>
        {{ restaurant.createdAt | fromNow }}
        <hr>
      </div> 
    </div>
  </div>
</template>

<script>
import { fromNowFilter } from './../utils/mixins'

export default {
  mixins: [fromNowFilter],
  // 從RestaurantsFeeds(父元件)傳來的資料，只能使用，不能修改
  props: {
    restaurants: {
      type: Array, // 傳進來的資料型態，沒寫的話預設值是array
      required: true // 標明這組資料一定要傳進來，才不會出錯
    }
  }
}
</script>

<style scoped>
small {
  font-size: 10px;
}
</style>