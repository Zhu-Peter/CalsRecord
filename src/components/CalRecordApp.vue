<template>
    <div>
        <v-container fluid="true">
            <v-row>
                <v-col>
                    <v-card width="100%" height="90%" class="elevation-1 my-8 pa-8">
                        <v-card-title class="mb-6">
                            <span class="text-h3">Enter a food for <span class="text-secondary text-capitalize">{{ currentSelection
                                    }}</span></span>
                        </v-card-title>
                        <!-- search bar -->
                        <v-text-field label="Search" v-model="search" prepend-icon="mdi-magnify"
                            @keyup="searchFood(search)"></v-text-field>
                        <div class="search result container" v-for="food in FoodList" :key="food.food_name">
                            <v-row class="pl-5">food items</v-row>
                            <v-row class="bg-grey-darken-1 mx-3">
                                <v-col offset="1">{{ food.food_name }}</v-col>
                                <v-col>{{ food.weight }}{{ food.weight_unit }}</v-col>
                                <v-col>Cals: {{ food.cals }}</v-col>
                            </v-row>
                        </div>
                        <div class="search result container" v-for="meal in MealList" :key="meal.name">
                            <v-row class="pl-5">meals</v-row>
                            <v-row class="bg-grey-darken-1 mx-3">
                                <v-col offset="1">{{ meal.name }}</v-col>
                                <v-col>Cals: {{ meal.cals }}</v-col>
                            </v-row>
                        </div>
                    </v-card>

                </v-col>
            </v-row>
            <v-row justify="space-between" class="px-8">
                <v-col>
                    <span class="text-h4 text-md-h2">
                        {{ date.toJSON().slice(0, 10) }}
                    </span>
                </v-col>
                <v-col cols="4" md="2">
                    <v-menu :close-on-content-click="false">
                        <template v-slot:activator="{ props }">
                            <v-btn color="secondary" v-bind="props" size="large" append-icon="mdi-calendar">
                                Date
                            </v-btn>
                        </template>
                        <v-date-picker v-model="date">
                        </v-date-picker>

                    </v-menu>

                </v-col>
            </v-row>
            <v-row>
                <v-col>
                    <v-expansion-panels variant="accordion">
                        <v-expansion-panel class="breakfast">
                            <v-expansion-panel-title>
                                <v-row>
                                    <v-col cols="7" sm="10" md="11">
                                        <div class="text-h5">Breakfast</div>
                                    </v-col>
                                    <v-col justify-self="end" cols="1">
                                        <v-btn flat color="primary" v-on:click="currentSelection = 'breakfast'">Add</v-btn>
                                    </v-col>
                                </v-row>
                            </v-expansion-panel-title>
                            <v-expansion-panel-text>
                                <v-row v-for="food in breakfast" :key="food.food_name">
                                    <v-col cols="4" sm="5">
                                        <div class="text-h5">{{ food.food_name }}</div>
                                    </v-col>
                                    <v-col cols="4" sm="5">
                                        <div class="text-h5">{{ food.cals }}</div>
                                    </v-col>
                                    <v-col justify-self="end" cols="1">
                                        <v-btn flat color="primary">Remove</v-btn>
                                    </v-col>
                                </v-row>
                            </v-expansion-panel-text>
                        </v-expansion-panel>
                        <v-expansion-panel class="lunch">
                            <v-expansion-panel-title>
                                <v-row>
                                    <v-col cols="7" sm="10" md="11">
                                        <div class="text-h5">Lunch</div>
                                    </v-col>
                                    <v-col justify-self="end" cols="1">
                                        <v-btn flat color="primary" @click="currentSelection = 'lunch'">Add</v-btn>
                                    </v-col>
                                </v-row>
                            </v-expansion-panel-title>
                        </v-expansion-panel>
                        <v-expansion-panel class="dinner">
                            <v-expansion-panel-title>
                                <v-row>
                                    <v-col cols="7" sm="10" md="11">
                                        <div class="text-h5">Dinner</div>
                                    </v-col>
                                    <v-col justify-self="end" cols="1">
                                        <v-btn flat color="primary" @click="currentSelection = 'dinner'">Add</v-btn>
                                    </v-col>
                                </v-row>
                            </v-expansion-panel-title>
                        </v-expansion-panel>
                        <v-expansion-panel class="snacks">
                            <v-expansion-panel-title>
                                <v-row>
                                    <v-col cols="7" sm="10" md="11">
                                        <div class="text-h5">Snacks/Other</div>
                                    </v-col>
                                    <v-col justify-self="end" cols="1">
                                        <v-btn flat color="primary" @click="currentSelection = 'snacks'">Add</v-btn>
                                    </v-col>
                                </v-row>
                            </v-expansion-panel-title>
                        </v-expansion-panel>
                    </v-expansion-panels>
                </v-col>
            </v-row>
        </v-container>
    </div>
</template>

<script>
import axios from 'axios';
import Cookies from 'vue-cookies';

export default {
    name: "CalRecordApp",
    data() {
        return {
            search: "",
            date: new Date(),
            currentSelection: "breakfast",
            FoodList: [],
            breakfast: [], lunch: [], dinner: [], snacks: [],
            userData: {}
        }
    },
    methods: {
        get_entries: function () {
            axios.request({
                method: 'get',
                url: 'http://127.0.0.1:5000/api/entry',
                headers: {
                    token: this.userData.token
                },
                data: {
                    email: this.email,
                    password: this.password
                }

            }).then((request) => {
                for (let i = 0; i < request.data.length; i++) {
                    if (request.data[i].breakfast) {
                        this.breakfast.push(request.data[i].breakfast);
                    }
                    if (request.data[i].lunch) {
                        this.lunch.push(request.data[i].lunch);
                    }
                    if (request.data[i].dinner) {
                        this.dinner.push(request.data[i].dinner);
                    }
                    if (request.data[i].snacks) {
                        this.snacks.push(request.data[i].snacks);
                    }
                }

            }).catch((error) => { console.log(error); this.error = error.response.data })
        },
        searchFood: function () {
            let temp = { name: this.search }
            axios.request({
                url: 'http://127.0.0.1:5000/api/food',
                params: temp

            }).then((response) => {
                console.log(response)
                this.FoodList = response.data
            }).catch((error) => { console.log(error); })
            // console.log({data: this.search})

            axios.request({
                url: 'http://127.0.0.1:5000/api/meals',
                params: temp

            }).then((response) => {
                console.log(response)
                this.FoodList = response.data
            }).catch((error) => { console.log(error); })

        },

    },
    beforeMount() {
        this.userData = Cookies.get('LoginData');
    },
}
</script>

<style scoped>
.breakfast {
    padding: 10px;
    margin: 10px;
    border-radius: 10px;
    border: 3px solid rgb(255, 255, 172);
}

.lunch {
    padding: 10px;
    margin: 10px;
    border-radius: 10px;
    border: 3px solid rgb(255, 203, 172);
}

.dinner {
    padding: 10px;
    margin: 10px;
    border-radius: 10px;
    border: 3px solid rgb(172, 194, 255);
}

.snacks {
    padding: 10px;
    margin: 10px;
    border-radius: 10px;
    border: 3px solid rgb(172, 255, 200);
}
</style>