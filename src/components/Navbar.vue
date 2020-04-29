<template>
    <v-app-bar
        app
        :color="color"
        dark
    >
        <v-toolbar flat color="transparent">
            <v-toolbar-title>SwapZilla</v-toolbar-title>
        </v-toolbar>
        <v-spacer></v-spacer>
        <v-tabs
            align-with-title
            v-model="tab"
        >
            <v-tab
                v-for="item in tabs"
                :key="item.tab"
            >
                {{ item.tab }}
            </v-tab>
        </v-tabs>
        <v-spacer></v-spacer>

        <v-btn v-if="hasFunding" x-large text @click="$emit('onFunding')">
            Funding
        </v-btn>
    </v-app-bar>
</template>

<script>

    export default {
        name: `Navbar`,

        props: {
            color: {
                type: String,
                default: `primary`
            },
            hasFunding: {
                type: Boolean,
                default: false
            },
            tabs: {
                type: Array,
                default: () => [
                    {
                        tab: 'tab 1'
                    },
                    {
                        tab: 'tab 2'
                    },
                    {
                        tab: 'tab 3'
                    },
                    {
                        tab: 'tab 4'
                    },
                ]
            }
        },

        data() {
            return {
                tab: null
            }
        }
    };
</script>
