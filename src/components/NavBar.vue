<template>
    <nav>
        <v-toolbar flat app>
            <v-app-bar-nav-icon class="text-grey" @click="toolbar_drawer = !toolbar_drawer"></v-app-bar-nav-icon>
            <v-toolbar-title class="font-weight-light text-primary">
                <span class="text-uppercase text-secondary">Cals</span>
                <span>Record</span>
            </v-toolbar-title>
            <v-btn flat color="grey">
                <span>Sign In</span>
                <v-icon right icon="mdi-exit-to-app" class="mx-1"></v-icon>
            </v-btn>
        </v-toolbar>
        <v-app>
            <v-navigation-drawer v-model="toolbar_drawer">
                <v-app-bar-nav-icon size="large" class="text-primary mt-4 ml-4"
                    @click="toolbar_drawer = !toolbar_drawer"></v-app-bar-nav-icon>
                <v-list class="ml-5">
                    <v-list-item v-for="link in links" :key="link.text" router :to="link.route">

                        <v-list-item-title>{{ link.text }}</v-list-item-title>

                    </v-list-item>
                </v-list>
            </v-navigation-drawer>
        </v-app>
    </nav>
</template>

<script>
export default {
    data() {
        return {
            toolbar_drawer: false,
            links: [
                { text: 'Dashboard', route: '/' },
                { text: 'Settings', route: '/About' },
            ]
        }
    },
}
</script>

<style scoped></style>