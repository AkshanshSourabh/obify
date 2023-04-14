<template>
<div>
    <app-header  @search = searchInBooks($event) ></app-header>
    <v-list>

        <v-list-item v-for="(item,i) in menu" :key="i">
            <v-list-item-avatar tile>
                <v-img :src="item.image"></v-img>
            </v-list-item-avatar>

            <v-list-item-content>
                <v-list-item-title>{{ item.name }}</v-list-item-title>
                <v-list-item-subtitle>Price: ${{ item.price }}</v-list-item-subtitle>
                <v-list-item-subtitle>Rating: {{ item.rating }}</v-list-item-subtitle>
            </v-list-item-content>

            <v-list-item-icon>
                <div>
                    <v-menu offset-y>
                        <template v-slot:activator="{ on, attrs }">
                            <v-btn v-bind="attrs" v-on="on" text @click="addToCart(item)">
                                Add to Cart
                            </v-btn>
                        </template>

                    </v-menu>
                </div>
            </v-list-item-icon>
        </v-list-item>
    </v-list>
</div>
</template>

  
<script>
import MenuList from '@/data/menuList.json'
import AppHeader from '@/components/AppHeader.vue'
import CartItems from './CartView.vue'

export default {
    data() {
        return {
            menu: MenuList,
            cart: []
        }
    },
    components: {
        AppHeader,
        CartItems 
    },
    methods:{
        searchInBooks(searchText){
          if (typeof searchText === "string"){
            this.menu = MenuList.filter(rec => rec.name.toLowerCase().includes(searchText.toLowerCase()))
          }
          else{
            this.menu = MenuList
          }
        },
        
        addToCart(item){
            this.cart.push(item)
        }
    }

}
</script>

  
<style lang="scss" scoped>

  </style>
