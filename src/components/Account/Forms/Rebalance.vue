<template>
    <v-col>
        <v-row class="d-block">
            <div class="caption ml-3 mb-3 dark--text">From</div>
            <v-select
                placeholder="Choose exchange"
                :items="items"
                solo
                background-color="light"
                append-icon="mdi-chevron-down"
                label="text"
                flat
            ></v-select>
        </v-row>
        <v-row class="d-block">
            <div class="caption ml-3 mb-3 dark--text">To</div>
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
            <v-autocomplete
                placeholder="Rebalance amount"
                background-color="light"
                append-icon="mdi-chevron-down"
                solo
                flat
            >
                <template v-slot:prepend-item>
                    <v-list-item>
                        <v-list-item-content>
                            <div>
                                <v-chip
                                    class="caption"
                                    color="rgba(42, 101, 145, 0.1)"
                                    label
                                    text-color="primary"
                                >
                                    Balance: <strong>0.04763864</strong>
                                </v-chip>
                            </div>
                        </v-list-item-content>
                    </v-list-item>
                </template>
                <template v-slot:no-data>
                    <v-list-item>
                        <v-list-item-content>
                            <div>
                                <v-btn
                                    class="white--text mr-2 pa-2 text-capitalize"
                                    v-for="percent in percents"
                                    :key="percent"
                                    small
                                    depressed
                                    color="label"
                                >{{ percent }}
                                </v-btn>
                            </div>
                        </v-list-item-content>
                    </v-list-item>
                </template>
            </v-autocomplete>
        </v-row>
        <v-row>
            <v-btn
                class="text-capitalize"
                color="primary"
                block
                x-large
            >
                Rebalance
            </v-btn>
        </v-row>
    </v-col>
</template>

<script>
    export default {
        name: `Rebalance`,

        components: {},

        props: ['currencies', 'items'],

        data: () => ({
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
