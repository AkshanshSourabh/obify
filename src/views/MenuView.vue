<template>
    <div>
      <v-menu offset-y>
        <template v-slot:activator="{ on }">
          <v-btn
            fab
            fixed
            bottom
            right
            v-on="on"
          >
            <v-icon>mdi-menu</v-icon>
          </v-btn>
        </template>
        <v-list>
          <v-list-group
            v-for="(category, index) in categories"
            :key="index"
            :prepend-icon="category.icon"
            no-action
          >
            <template v-slot:activator>
              <v-list-item-title>
                {{ category.title }}
              </v-list-item-title>
            </template>
            <v-list-item
              v-for="(item, i) in category.items"
              :key="i"
              @click="addItem(item)"
            >
              <v-list-item-content>
                <v-list-item-title>{{ item.name }}</v-list-item-title>
                <v-list-item-subtitle>{{ item.price }}</v-list-item-subtitle>
              </v-list-item-content>
              <v-list-item-action>
                <v-btn small color="primary" @click="addItem(item)">
                  Add
                </v-btn>
              </v-list-item-action>
            </v-list-item>
          </v-list-group>
        </v-list>
      </v-menu>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        categories: [
          {
            title: 'Breads',
            icon: 'mdi-bread-slice',
            items: [
              { name: 'Baguette', price: '$5' },
              { name: 'Croissant', price: '$3' },
              { name: 'Pretzel', price: '$4' },
            ]
          },
          {
            title: 'Vegetarian',
            icon: 'mdi-carrot',
            items: [
              { name: 'Caesar Salad', price: '$8' },
              { name: 'Margherita Pizza', price: '$12' },
              { name: 'Veggie Burger', price: '$10' },
            ]
          },
          {
            title: 'Non-Vegetarian',
            icon: 'mdi-steak',
            items: [
              { name: 'Cheeseburger', price: '$12' },
              { name: 'Chicken Caesar Salad', price: '$10' },
              { name: 'Pepperoni Pizza', price: '$14' },
            ]
          },
        ],
      }
    },
    methods: {
      addItem(item) {
        // Add item to cart or perform other logic
        console.log('Added item:', item)
      },
    },
  }
  </script>
  