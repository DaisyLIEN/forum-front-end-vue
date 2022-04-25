<template>
  <div id="restaurant-forum">
    
    <!-- 載入Navbar -->
    <Navbar />

    <main role="main" class="mt-5 bg-white">
      <router-view />
    </main>

  </div>
</template>

<script>
import "bootstrap";
import "bootstrap/dist/css/bootstrap.min.css";
import Navbar from "./components/NavBar.vue";

export default {
  // name: 'App'
  components: {
    Navbar, // Navbar: Navbar的縮寫
  },
};
</script>
