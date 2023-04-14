<template>
    <v-bottom-navigation app>
    <v-btn value="recent" @click= "$router.push('/menu')">
      <span>Menu</span>

      <v-icon>mdi-silverware</v-icon>
    </v-btn>

    <v-btn value="favorites" @click= "$router.push('/cart')">
      <span>Cart</span>

      <v-icon>mdi-cart</v-icon>
    </v-btn>

    <v-btn value="nearby" @click= "$router.push('/payment')">
      <span>Account</span>

      <v-icon>mdi-account</v-icon>
    </v-btn>
  </v-bottom-navigation>
</template>

<script>
    export default {
        
    }
</script>

<style lang="scss" scoped>

</style>