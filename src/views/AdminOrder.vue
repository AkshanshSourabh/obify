<template>
    <div>
      <h1>Real-Time Kitchen Orders</h1>
      <div v-for="(orders, table) in orderList" :key="table">
        <h2>Table {{table}}</h2>
        <ul>
          <li v-for="order in orders" :key="order.id">
            <div>{{order.name}} ({{order.time}})</div>
            <div>
              <button @click="acceptOrder(order)">Accept</button>
              <button @click="rejectOrder(order)">Reject</button>
            </div>
          </li>
        </ul>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        orderList: {},
      };
    },
    created() {
      // Set up real-time listener for incoming orders
      this.$socket.on("new-order", (order) => {
        if (!this.orderList[order.table]) {
          this.$set(this.orderList, order.table, []);
        }
        this.orderList[order.table].push(order);
      });
    },
    methods: {
      acceptOrder(order) {
        // Handle accepting order logic here
        console.log("Accepted order:", order);
      },
      rejectOrder(order) {
        // Handle rejecting order logic here
        console.log("Rejected order:", order);
      },
    },
  };
  </script>