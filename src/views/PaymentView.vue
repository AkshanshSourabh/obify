<template>
    <div class="pa-3 text-no-wrap rounded-sm">
        <v-row>
            <v-col cols="10" sm="10" offset-sm="1" md="8" offset-md="2" offset="1">
                <v-app-bar-nav-icon> </v-app-bar-nav-icon>
                <v-toolbar-title>Payment Options</v-toolbar-title><br>
                <h3>UPI</h3>
                <v-checkbox v-model="ex4" label="GPay" hide-details></v-checkbox>
                <v-checkbox v-model="ex4" label="PhonePe" hide-details></v-checkbox>
                <v-checkbox v-model="ex4" label="Paytm" hide-details></v-checkbox>
                <br>
                <h3>Card</h3>
                <v-checkbox v-model="ex4" label="Debit Card" hide-details></v-checkbox>
                <v-checkbox v-model="ex4" label="Credit Card" hide-details></v-checkbox>
                <br>
                <v-checkbox v-model="ex4" label="Pay Via Cash" hide-details></v-checkbox>

                

            </v-col>
        </v-row>

        <v-spacer></v-spacer>
    </div>
</template>
    
<script>

export default {

}
</script>
    
<style lang="scss" scoped></style>