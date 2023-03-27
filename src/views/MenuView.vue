<template>
  <div>
      <app-header title="Books"></app-header>
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
                              <v-btn v-bind="attrs" v-on="on" text>
                                  Add to Cart
                              </v-btn>
                          </template>
                         
                      
                       </v-menu>                  </div>
              </v-list-item-icon>
          </v-list-item>
      </v-list>
  
  </div>
  </template>
  
  <script>
  import MenuList from '@/data/menuList.json'
  import AppHeader from '@/components/AppHeader.vue'
  
  export default {
      data() {
          return {
              menu: MenuList,
  
          }
      },
      components: {
          AppHeader
      },
  
  }
  </script>
  
  <style lang="scss" scoped>
  
  </style>
  