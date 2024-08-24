<template>
    <div>
        <v-container fluid="true">
            <v-row>
                <v-col>
                    <v-card width="100%" height="90%" class="elevation-1 my-8 py-8" justify-center>
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
                    <v-row class="breakfast">
                        <v-col></v-col>
                        <v-col>
                            <v-btn color="primary" @click="addBreakfast">Add Breakfast</v-btn>
                        </v-col>
                    </v-row>
                    <v-row class="lunch">
                        <v-col></v-col>
                        <v-col>
                             <v-btn color="primary" @click="addLunch">Add Lunch</v-btn>
                         </v-col>
                    </v-row>
                    <v-row class="dinner">
                        <v-col></v-col>
                        <v-col>
                            <v-btn color="primary" @click="addDinner">Add Dinner</v-btn>
                        </v-col>
                    </v-row>
                    <v-row class="snacks">
                        <v-col></v-col>
                        <v-col>
                             <v-btn color="primary" @click="addSnacks">Add Snacks</v-btn>
                         </v-col>
                    </v-row>
                    <v-row class="snacks">

                    </v-row>
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

<style scoped></style>