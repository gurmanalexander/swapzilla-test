<template>
    <v-dialog
        persistent
        v-model="dialog"
        width="780"
    >
        <v-card>
            <v-toolbar class="pa-3" flat>
                <v-tabs v-model="tab" color="dark" slider-size="4">
                    <v-tab
                        key="Deposit"
                        href="#tab-Deposit"
                        class="px-0 mx-5 title text-capitalize"
                    >Deposit</v-tab>
                    <v-tab
                        key="Withdraw"
                        href="#tab-Withdraw"
                        class="px-0 mx-5 title text-capitalize"
                    >Withdraw</v-tab>
                    <v-tab
                        key="Rebalance"
                        href="#tab-Rebalance"
                        class="px-0 mx-5 title text-capitalize"
                    >Rebalance</v-tab>
                </v-tabs>
                <v-spacer></v-spacer>

                <v-btn icon @click="$emit('closed')">
                    <v-icon class="display-1">mdi-close</v-icon>
                </v-btn>
            </v-toolbar>
            <v-card-text class="pa-5">
                <v-container fluid>
                    <v-tabs-items v-model="tab">
                        <v-tab-item key="Deposit" value="tab-Deposit">
                            <v-row class="d-flex justify-center">
                                <v-col cols="12" sm="6">
                                    <v-row>
                                        <deposit :items="items" :currencies="currencies"></deposit>
                                    </v-row>
                                </v-col>
                            </v-row>
                        </v-tab-item>
                        <v-tab-item key="Withdraw" value="tab-Withdraw">
                            <v-row class="d-flex justify-center">
                                <v-col cols="12" sm="6">
                                    <v-row>
                                        <withdraw :items="items" :currencies="currencies"></withdraw>
                                    </v-row>
                                </v-col>
                            </v-row>
                        </v-tab-item>
                        <v-tab-item key="Rebalance" value="tab-Rebalance">
                            <v-row class="d-flex justify-center">
                                <v-col cols="12" sm="6">
                                    <v-row>
                                        <rebalance :items="items" :currencies="currencies"></rebalance>
                                    </v-row>
                                </v-col>
                            </v-row>
                        </v-tab-item>
                    </v-tabs-items>
                </v-container>
            </v-card-text>
        </v-card>
    </v-dialog>
</template>

<script>
    import Rebalance from "./Forms/Rebalance";
    import Withdraw from "./Forms/Withdraw";
    import Deposit from "./Forms/Deposit";

    export default {
        name: `AccountModal`,

        components: {Rebalance, Withdraw, Deposit},

        props: {
            dialog: Boolean,
            tab: {
                type: String,
                default: `tab-Deposit`
            }
        },

        data: () => ({
            // tab: `tab-Deposit`,
            sum: null,
            currencies: [
                {
                    text: `USD`,
                    value: `USD`
                },
                {
                    text: `EUR`,
                    value: `EUR`
                },
                {
                    text: `Bitcoin`,
                    value: `Bitcoin`
                },
            ],
            items: [
                {
                    text: `Kraken`,
                    value: `Kraken`
                },
                {
                    text: `Else`,
                    value: `Else`
                },
            ],
            percents: [
                `10%`,
                `25%`,
                `50%`,
                `100%`,
                `split`
            ]
        }),
    };
</script>
