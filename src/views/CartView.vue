<template>
<div>
    <cart-items :cart="cart" />

    <v-list>

        <v-list-item v-for="(item,i) in cart" :key="i">

            <v-list-item-content>
                <v-list-item-title>{{ item.name }}</v-list-item-title>
                <span class="buttons">
                    <v-btn class="mx-2" fab dark small color="primary" @click="decrement()">
                        <v-icon dark>
                            mdi-minus
                        </v-icon>
                    </v-btn>
                    {{ count }}
                    <v-btn class="mx-2" fab dark small color="primary" @click="increment()">
                        <v-icon dark>
                            mdi-plus
                        </v-icon>
                    </v-btn>
                </span>

            </v-list-item-content>

            <div>
                <v-list-item-title> ${{ item.price * count}}</v-list-item-title>
            </div>

        </v-list-item>
    </v-list>
    <div>
        <v-btn class="mx-2" fab dark small color="primary">
            <v-icon dark>
                mdi-plus
            </v-icon>
        </v-btn>
        Add More Items

    </div>
    <input type="text" placeholder="Add Cooking Instruction">

    <v-bottom-navigation >
        <!-- Total: ${{ item.price * count}} -->
        <v-btn color="deep-purple accent-4" text>
            <span>Proceed to Payment</span>

            <v-icon>mdi-cart</v-icon>
        </v-btn>

    </v-bottom-navigation>

    <!-- <v-responsive id="hide-on-scroll-example" class="overflow-y-auto" max-height="600">
        <v-responsive height="1500"></v-responsive>
    </v-responsive> -->

</div>
</template>

<script>
import MenuList from '@/data/menuList.json'
export default {
    data() {
        return {
            menu: MenuList,
            count: 0

        }
    },
    props: {
    cart: {
      type: Array,
      required: true
    }
  },
    methods: {
        increment() {
            this.count++;

        },
        decrement() {
            this.count--;

        }
    },
}
</script>

<style lang="scss" scoped>
.buttons {
    display: flex;
    justify-content: flex-end;
}
</style>
