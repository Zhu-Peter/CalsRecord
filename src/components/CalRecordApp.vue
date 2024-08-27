<template>
    <div>
        <v-container fluid="true">
            <v-row>
                <v-col>
                    <v-card width="100%" height="90%" class="elevation-1 my-8 pa-8">
                        <v-card-title class="mb-6">
                            <span class="text-h3">Enter a food for <span class="text-secondary">{{ currentSelection
                                    }}</span></span>
                        </v-card-title>
                        <!-- search bar -->
                        <v-text-field label="Search" v-model="search" prepend-icon="mdi-magnify"></v-text-field>

                    </v-card>

                </v-col>
            </v-row>
            <v-row justify="space-between" class="px-8">
                <v-col>
                    <span class="text-h4 text-md-h2">
                        {{ date.toJSON().slice(0,10) }}
                    </span>
                </v-col>
                <v-col cols="4" md="2">
                    <v-menu>
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
                                        <v-btn flat color="primary">Add</v-btn>
                                    </v-col>
                                </v-row>
                            </v-expansion-panel-title>
                            <v-expansion-panel-text>
                                <v-row v-for="food in breakfast" :key="food.name">
                                    <v-col cols="4" sm="5">
                                        <div class="text-h5">{{ food.name }}</div>
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
                                        <v-btn flat color="primary">Add</v-btn>
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
                                        <v-btn flat color="primary">Add</v-btn>
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
                                        <v-btn flat color="primary">Add</v-btn>
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
export default {
    name: "CalRecordApp",
    data() {
        return {
            search: "",
            date: new Date(),
            currentSelection: "Breakfast",
            breakfast: [], lunch: [], dinner: [], snacks: []
        }
    }
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