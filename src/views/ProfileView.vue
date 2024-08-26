<template>
    <div>
        <v-container>
            <v-row>
                <v-col>
                    <v-card>
                        <v-card-title>
                            <v-card-title-text>
                                <span class="headline">Profile</span>
                            </v-card-title-text>
                        </v-card-title>

                        <v-card-text>
                            <v-container>
                                <v-row>
                                    <v-col>
                                        <span>First Name: {{userData.first_name}}</span>
                                        <v-text-field v-model="form.first_name" label="First Name"></v-text-field>
                                    </v-col>
                                    <v-col>
                                        <span>Last Name: {{userData.last_name}}</span>
                                        <v-text-field v-model="form.last_name" label="Last Name"></v-text-field>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col>
                                        <span>Email: {{userData.email}}</span>
                                        <v-text-field v-model="form.email" label="Email"></v-text-field>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col>
                                        <v-text-field v-model="form.password" label="Password"></v-text-field>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col>
                                        <v-text-field v-model="form.password_check" label="Re-enter Password"></v-text-field>
                                    </v-col>
                                </v-row>
                            </v-container>
                            <v-btn color="error" @click="logOut">Log Out</v-btn>
                        </v-card-text>
                    </v-card>
                </v-col>
            </v-row>
        </v-container>
    </div>
</template>

<script>
import axios from 'axios';
import Cookies from 'vue-cookies';

export default {
    name: 'ProfileView',
    data() {
        return {
            userData: {
            },
            form: {
                email: '',
                first_name: '',
                last_name: '',
                password: '',
                password_check: '',
            },
            password_delete: '',
            error: '',
        }
    },
    methods: {
        
        logOut: function () {
            axios.request({
                method: 'delete',
                url: 'http://127.0.0.1:5000/api/login',
                headers: {
                    "token": this.userData['token']
                }
            }).then(() => {
                Cookies.remove('LoginData');
                this.$router.push(`/`)
            }).catch(() => {
                Cookies.remove('LoginData');
                this.$router.push(`/`)
            })
        },
        changeInfo: function () {
            let updateData = {};
            Object.keys(this.form).forEach((key) => {
                if (this.form[key] !== '') {
                    if (key !== 'password_check') {
                        if (key == 'password') {
                            if (this.form.password == this.form.password_check) {
                                updateData[key] = this.form[key];
                            }
                        } else {
                            updateData[key] = this.form[key];
                        }
                    }
    
                }
            });
            axios.request({
                method: 'patch',
                url: 'http://127.0.0.1:5000/api/user',
                headers: {
                    "token": this.userData['token']
                },
                data: updateData,
            }).then((response) => {
                console.log(response);
                Object.keys(updateData).forEach((key) => {
                    if (updateData[key] !== '') {
                        if (key !== 'password') {
                            this.userData[key] = updateData[key];
    
                        }
    
                    }
                });
                Cookies.set('LoginData', this.userData)
            }).catch(error => { console.log(error) })
    
        },
        DeleteProfile: function () {
            if (!this.toggleDelete) {
                this.toggleDelete = !this.toggleDelete
            } else {
                axios.request({
                    method: 'delete',
                    url: 'http://127.0.0.1:5000/api/user',
                    headers: {
                        "token": this.userData['token']
                    },
                    data: { password: this.password_delete }
                }).then((response) => {
                    console.log(response);
                    this.error = '';
                    this.logOut();
                }).catch(error => { console.log(error); this.error = error.response.data })
    
            }
        },
    },
    beforeMount() {
        let data = Cookies.get('LoginData');
        if (Object.keys(data).length == 2) {
            axios.request({
                url: 'http://127.0.0.1:5000/api/user',
                params: this.userData
            }).then(response => {
                console.log(response);
                this.userData = { ...data, ...response.data[0] };
                let tempData = JSON.stringify(this.userData);
                Cookies.set('LoginData', tempData)
            }).catch(error => { console.log(error) })
        }
        this.userData = data;
    },
}
</script>

<style scoped></style>