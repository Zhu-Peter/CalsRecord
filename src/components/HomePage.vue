<template>
<div class="background" image="https://images.pexels.com/photos/1391487/pexels-photo-1391487.jpeg">
        <v-carousel hide-delimiters show-arrows="hover">
          <v-carousel-item src="https://images.pexels.com/photos/1391487/pexels-photo-1391487.jpeg"
            cover></v-carousel-item>

          <v-carousel-item src="https://images.pexels.com/photos/940302/pexels-photo-940302.jpeg"
            cover></v-carousel-item>

          <v-carousel-item src="https://images.pexels.com/photos/9430363/pexels-photo-9430363.jpeg"
            cover></v-carousel-item>
        </v-carousel>
        <v-container style="margin-top: -450px; margin-bottom: 2px;">
          <v-card flat class="pa-3" height="400">
            <v-container class="text-sm-h4 text-md-h3 text-center mb-3">
              <div class="pa-sm-5" style="font-family: Arial, Helvetica, sans-serif;">
                Sign up today to access our fully functional free app! Track your calories, create your own meals out of
                common ingredients, and much more!
              </div>

            </v-container>
            <v-row wrap class="justify-center">
              <v-col cols="8" md="3">
                <v-btn block outline color="secondary" class="pa-6">Sign up now!</v-btn>
              </v-col>
              <v-col cols="8" md="3">
                <v-btn block outline color="primary" class="pa-6">Sign in</v-btn>
              </v-col>
            </v-row>
          </v-card>

        </v-container>
        <v-container>
          <v-row wrap no-gutters class="justify-end">
            <v-col cols="12" sm="4" >
              <v-row no-gutters>
                <v-img 
                  src="https://images.pexels.com/photos/2374946/pexels-photo-2374946.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"></v-img>

              </v-row>
              <v-row no-gutters>
                <v-img 
                  src="https://images.pexels.com/photos/326281/pexels-photo-326281.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"></v-img>

              </v-row>
              <v-row no-gutters>
                <v-img 
                  src="https://images.pexels.com/photos/257816/pexels-photo-257816.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"></v-img>

              </v-row>
            </v-col>
            <v-col cols="12" sm="5">
              <v-img
                src="https://images.pexels.com/photos/6551070/pexels-photo-6551070.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"></v-img>

            </v-col>
            
            <v-col cols="12" sm="3" class="mx-n3 mt-5">
              <v-card class="text-center pa-2">
                <div class="text-h5 ma-5">
                  Want more resources on a healthy diet and meal prep?
                </div>
                <v-btn color="primary ma-3 ">Click here</v-btn>
              </v-card>

            </v-col>
          </v-row>
        </v-container>

      </div>
</template>

<script>
    export default {
        name: 'HomePage'
    }
</script>

<style scoped>

</style>