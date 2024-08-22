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
            <v-container class="text-sm-h3 text-center">
              <div class="pa-6" style="font-family: Arial, Helvetica, sans-serif;">
                Sign up today to access our fully functional free app! Track your calories, create your own meals out of common ingredients, and much more!
              </div>

            </v-container>
            <v-layout row wrap class="justify-center">
              <v-flex xs12 md6 >
                <v-btn block outline color="secondary" class="pa-6 mr-10">Sign up now!</v-btn>
              </v-flex>
              <v-flex xs12 md6>
                <v-btn block outline color="primary" class="pa-6 ml-10">Sign in</v-btn>
              </v-flex>
            </v-layout>
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
