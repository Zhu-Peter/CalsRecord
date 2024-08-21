<template>
  <div class="home">
    <!-- <h1>This is the home page</h1> -->
    <div v-if="isLoggedIn">

    </div>
    <div v-else>
      <div class="background" image="https://images.pexels.com/photos/1391487/pexels-photo-1391487.jpeg">
        <v-carousel hide-delimiters>
          <v-carousel-item src="https://images.pexels.com/photos/1391487/pexels-photo-1391487.jpeg" cover></v-carousel-item>

          <v-carousel-item src="https://images.pexels.com/photos/940302/pexels-photo-940302.jpeg" cover></v-carousel-item>

          <v-carousel-item src="https://images.pexels.com/photos/9430363/pexels-photo-9430363.jpeg" cover></v-carousel-item>
        </v-carousel>
        <v-container style="margin-top: -450px;">
          <v-card flat class="pa-3" height="400">
            
          </v-card>

        </v-container>
        
      </div>
    </div>

  </div>
</template>

<script>


export default {
  name: 'HomeView',
  components: {

  },
  data() {
    return {
      isLoggedIn: false,
    }
  },
}
</script>
