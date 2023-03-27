<template>
    <div class="app-header">
           <v-row>
            <v-col>
                <v-text-field solo label="Search" append-icon="mdi-magnify">
                </v-text-field>
            </v-col>
        </v-row>
    </div>
    </template>
    
    <script>
    export default {
        props: {
            title: {
                type: String
            },
        },
    }
    </script>
    
    <style lang="scss" scoped>
    .app-header {
        padding: 1rem
    }
    </style>
    