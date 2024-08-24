<template>
    <div>
        <v-container fluid="true">
            <v-row>
                <v-col>
                    <v-card width="100%" height="90%" class="elevation-1 my-8 pa-8">
                        <v-card-title-text>
                            <span class="headline">Enter a food</span>
                        </v-card-title-text>
                        <!-- search bar -->
                        <v-text-field label="Search" v-model="search" prepend-icon="mdi-magnify"></v-text-field>

                    </v-card>

                </v-col>
            </v-row>
            <v-row>
                <v-col>
                    <v-card class="breakfast">
                        <v-row>
                            <v-col></v-col>
                            <v-col>
                                <v-btn color="primary" @click="addBreakfast">Add Breakfast</v-btn>
                            </v-col>
                        </v-row>
                    </v-card>
                    <v-card class="lunch">
                        <v-row>
                            <v-col></v-col>
                            <v-col>
                                 <v-btn color="primary" @click="addLunch">Add Lunch</v-btn>
                             </v-col>
                        </v-row>
                    </v-card>
                    <v-card class="dinner">
                        <v-row>
                            <v-col></v-col>
                            <v-col>
                                <v-btn color="primary" @click="addDinner">Add Dinner</v-btn>
                            </v-col>
                        </v-row>
                    </v-card>
                    <v-card class="snacks">
                        <v-row>
                            <v-col></v-col>
                            <v-col justify="end">
                                 <v-btn color="primary" @click="addSnacks">Add Snacks</v-btn>
                             </v-col>
                        </v-row>
                    </v-card>
                </v-col>
            </v-row>
        </v-container>
    </div>
</template>

<script>
export default {
    name: "CalRecordApp",
    data() {
        return {
            search: ""
        }
    }
}
</script>

<style scoped>
.breakfast{
    padding: 10px;
    margin: 10px;
    border-radius: 10px;
    border: 3px solid rgb(255, 255, 172);
}
.lunch{
    padding: 10px;
    margin: 10px;
    border-radius: 10px;
    border: 3px solid rgb(255, 203, 172);
}
.dinner{
    padding: 10px;
    margin: 10px;
    border-radius: 10px;
    border: 3px solid rgb(172, 194, 255);
}
.snacks{
    padding: 10px;
    margin: 10px;
    border-radius: 10px;
    border: 3px solid rgb(172, 255, 200);
}

</style>