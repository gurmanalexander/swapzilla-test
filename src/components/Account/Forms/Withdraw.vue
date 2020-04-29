<template>
    <v-col>
        <v-row>
            <v-select
                placeholder="Choose exchange"
                :items="items"
                solo
                background-color="light"
                append-icon="mdi-chevron-down"
                flat
            ></v-select>
        </v-row>
        <v-row>
            <v-select
                placeholder="Choose currency"
                :items="currencies"
                solo
                background-color="light"
                append-icon="mdi-chevron-down"
                flat
            ></v-select>
        </v-row>
        <v-row>
            <v-text-field
                placeholder="Withdraw amount"
                background-color="light"
                solo
                flat
                v-model="sum"
            >
                <template v-slot:append>
                    <v-btn
                        class="text-capitalize"
                        color="label"
                        small
                        dark
                        depressed
                        @click="sum = 1000"
                    >
                        max
                    </v-btn>
                </template>
            </v-text-field>
        </v-row>
        <v-row>
            <v-btn
                class="text-capitalize"
                color="primary"
                block
                x-large
            >
                Withdraw
            </v-btn>
        </v-row>
    </v-col>
</template>

<script>
    export default {
        name: `Withdraw`,

        components: {},

        props: ['currencies', 'items'],

        data() {
            return {
                sum: null
            }
        }
    };
</script>
