<template>
    <div>
        <v-container class="background_with_image bg-grey-darken-4" fluid fill-height>
            <v-row justify="center">
                <v-card width="70%" height="90%" class="elevation-1 my-8 py-8" justify-center>
                    <v-card-title>
                        <v-card-title-text>
                            <span class="headline">Login</span>
                        </v-card-title-text>
                    </v-card-title>
                    <v-card-text>
                        <v-container>
                            <v-row>
                                <v-col cols="12">
                                    <v-text-field label="Email" prepend-icon="mdi-email" v-model="email"
                                        required></v-text-field>
                                </v-col>
                            </v-row>
                            <v-row>
                                <v-col cols="12">
                                    <v-text-field label="Password" prepend-icon="mdi-lock" v-model="password"
                                        type="password" required></v-text-field>
                                </v-col>
                            </v-row>
                            <v-row justify="end">
                                <v-col cols="6" sm="3" md="2">
                                    <v-btn class="login_btn" color="primary" @click="login">Login</v-btn>
                                </v-col>
                            </v-row>
                            <v-row>
                                <v-col>
                                    <v-alert v-if="error" color="error">{{ error }}</v-alert>
                                </v-col>
                            </v-row>
                            <v-row justify="center">
                                <v-col class="text-center text-body-1">
                                    <span>Don't have an account? <router-link to="/signup">Register</router-link></span>
                                </v-col>
                            </v-row>
                        </v-container>
                    </v-card-text>
                </v-card>
            </v-row>
        </v-container>
    </div>
</template>

<script>
import axios from 'axios';
import Cookies from 'vue-cookies';

export default {
    name: 'LoginPage',
    data() {
        return {
            email: '',
            password: '',
            error: '',
            token: '',
        }
    },
    methods: {
        login: function () {
            this.error = '';
            axios.request({
                method: 'post',
                url: 'http://127.0.0.1:5000/api/login',
                data: {
                    email: this.email,
                    password: this.password
                }

            }).then((request) => {
                // console.log(request.data);
                this.token = JSON.stringify(request.data);
                Cookies.set('LoginData', this.token)
                this.$router.push(`/`)

            }).catch((error) => { console.log(error); this.error = error.response.data })
        },
    }

}
</script>

<style scoped>
.background_with_image {
    background-image: url('https://images.pexels.com/photos/1247676/pexels-photo-1247676.jpeg');
    background-size: cover;
    background-position: center;
    height: 100vh;
    width: 100vw;
    display: flex;
    /* filter: blur(5px) brightness(84%); */

}

.v-card-title {
    margin-top: 30px;
    margin-left: 30px;
    margin-bottom: 30px;
}

/* .login_btn{
    margin-right: 30px;
} */
</style>