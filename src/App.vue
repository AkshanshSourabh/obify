<template>
<v-app>
    <v-app-bar app color="primary" dark>
        <div class="d-flex align-center">
            <v-img alt="Vuetify Logo" class="shrink mr-2" contain src="@/assets/logo.png" transition="scale-transition" width="60" />

            <p><h3>{{ $const.APP_NAME }}</h3></p>
        </div>

        <v-spacer></v-spacer>

        <v-btn text value="recent" @click="$router.push('/')">
            <v-icon>mdi-account-circle</v-icon>

            <!-- <v-icon>mdi-open-in-new</v-icon> -->
        </v-btn>
    </v-app-bar>

    <v-main>
        <router-view />
    </v-main>
    <bottom-navbar></bottom-navbar>
</v-app>
</template>

<script>
import BottomNavbar from '@/components/BottomNavbar.vue';

export default {
    name: "App",
    data: () => ({
        //
    }),
    components: {
        BottomNavbar
    }
};
</script>
