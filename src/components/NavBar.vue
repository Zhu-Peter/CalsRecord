<template>

    <nav>
        <v-toolbar app>
            <v-menu>
                <template v-slot:activator="{ props }">
                    <v-btn color="primary" dark v-bind="props">
                        <v-app-bar-nav-icon class="text-grey pb-2"
                            @click="toolbar_drawer = !toolbar_drawer"></v-app-bar-nav-icon>
                    </v-btn>
                </template>
                <v-list class="py-4">
                    <v-list-item v-for="link in links" :key="link.text" router :to="link.route">
                        <template v-slot:prepend>
                            <v-icon :icon="link.icon"></v-icon>
                        </template>
                        <v-list-item-title>{{ link.text }}</v-list-item-title>
                    </v-list-item>
                </v-list>
            </v-menu>
            <v-app-bar-title class="font-weight-light text-primary">
                <router-link to="/" style="text-decoration: none;" class="text-primary">
                    <span class="text-uppercase text-secondary">Cals</span>
                    <span>Record</span>
                </router-link>
            </v-app-bar-title>
            <v-btn flat color="grey" router to="/login">
                <span>Sign In</span>
                <v-icon right icon="mdi-exit-to-app" class="mx-1"></v-icon>
            </v-btn>
        </v-toolbar>

        <!-- <v-navigation-drawer app v-model="toolbar_drawer">
                <v-list class="ml-2 mt-4">
                    <v-list-item v-for="link in links" :key="link.text" router :to="link.route">
                        <template v-slot:prepend>
                            <v-icon :icon="link.icon"></v-icon>
                        </template>
                        <v-list-item-title>{{ link.text }}</v-list-item-title>
                    </v-list-item>
                </v-list>
            </v-navigation-drawer> -->
    </nav>

</template>

<script>
export default {
    name: "NavBar",
    data() {
        return {
            toolbar_drawer: false,
            links: [
                { text: 'Dashboard', route: '/', icon: 'mdi-view-dashboard' },
                { text: 'About', route: '/About', icon: 'mdi-information' },
                { text: 'Settings', route: '/', icon: 'mdi-account-box' }
            ]
        }
    },
}
</script>

<style scoped></style>