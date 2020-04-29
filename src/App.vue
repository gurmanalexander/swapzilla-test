<template>
    <v-app>
        <navbar :color="color" :tabs="navbarTabs" :has-funding="funding" @onFunding="open({tab: 'Rebalance'})"></navbar>
        <v-content>
            <v-container
                class="fill-height"
                fluid
            >
                <v-row align="center" justify="center" class="flex-column">
                    <v-btn class="my-3" @click="open({ tab: 'Withdraw' })">open withdraw</v-btn>
                    <v-btn class="my-3" @click="color = color ? undefined : 'dark'">toggle color</v-btn>
                    <v-btn class="my-3" @click="navbarTabs = navbarTabs ? undefined : [{ tab: 'Custom tab' }]">toggle tabs</v-btn>
                    <v-btn class="my-3" @click="funding = funding ? undefined : true">toggle funding</v-btn>
                    <div class="pa-10" style="height: 100vh">
                        content for scrolling
                    </div>
                </v-row>
            </v-container>
        </v-content>
        <account-modal :dialog="dialog" :tab="tab" @closed="dialog = false"></account-modal>
    </v-app>
</template>

<script>
    import AccountModal from "./components/Account/AccountModal";
    import Navbar from "./components/Navbar";
    export default {
        name: `App`,

        components: {Navbar, AccountModal},

        data: () => ({
            dialog: false,
            color: undefined,
            navbarTabs: undefined,
            funding: true,
            tab: `tab-Deposit`,
        }),

        methods: {
            open({tab}) {
                this.dialog = true
                this.tab = `tab-${tab}`
            }
        }
    };
</script>
