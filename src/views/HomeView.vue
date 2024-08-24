<template>
  <div class="home">
    <!-- <h1>This is the home page</h1> -->
    <div v-if="isLoggedIn">
      <CalRecordApp/>
    </div>
    <div v-else>
      <HomePage />
    </div>

  </div>
</template>

<script>
import HomePage from '@/components/HomePage.vue';
import CalRecordApp from '@/components/CalRecordApp.vue';
export default {
  name: 'HomeView',
  components: {
    HomePage, CalRecordApp
  },
  data() {
    return {
      isLoggedIn: true,
    }
  },
}
</script>
