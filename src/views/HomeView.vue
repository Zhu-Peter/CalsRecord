<template>
  <div class="home">
    <!-- <h1>This is the home page</h1> -->
    <div v-if="isLoggedIn">
      <CalRecordApp />
    </div>
    <div v-else>
      <HomePage />
    </div>

  </div>
</template>

<script>
import HomePage from '@/components/HomePage.vue';
import CalRecordApp from '@/components/CalRecordApp.vue';

import Cookies from 'vue-cookies';
import axios from 'axios';

export default {
  name: 'HomeView',
  components: {
    HomePage, CalRecordApp
  },
  data() {
    return {
      isLoggedIn: false,
      userData: {
        username: ''
      },
    }
  },
  beforeMount() {
    let data = Cookies.get('LoginData');
    if (!(data === null)) {
      this.isLoggedIn = true;
      if (Object.keys(data).length > 2) {
        this.userData = data
      } else {
        axios.request({
          url: 'http://127.0.0.1:5000/api/user',
          params: data
        }).then((response) => {
          // console.log({ ...data, ...response.data[0] });
          this.userData = { ...data, ...response.data[0] };
          let tempData = JSON.stringify(this.userData);
          Cookies.set('LoginData', tempData)
        });

      }

    }
  },
}
</script>
