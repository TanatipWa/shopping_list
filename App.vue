<template>
  <div id="app">
    <h1>{{ total }}</h1>
    <table>
      <tr v-for="(order, index) in orders" v-bind:key="(order, index)">
        <td>{{ index + 1 }}. {{ order.text }}</td>
        <td align="right">{{ order.price }} BATH</td>
        <td>
          <b-button type="is-primary" @click="changeOrderAtIndex(index)"
            >Modify</b-button
          >
          <b-button type="is-danger" @click="removeOrderAtIndex(index)"
            >Delete</b-button
          >
        </td>
      </tr>

      <tr>
        <td><b-input type="text" v-model="newOrder" /></td>
        <td><b-input type="text" v-model="newPrice" /></td>
        <td><b-button type="is-success" @click="addOrder">Add</b-button></td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      newOrder: "",
      newPrice: "",
      total: 0,
      orders: [
        { text: "iPhone 11 Pro", price: 42900 },
        { text: "Macbook Air", price: 36990 },
        { text: "Honda CT 125", price: 84900 },
      ],
    };
  },
  methods: {
    addOrder: function() {
      this.orders.push({ text: this.newOrder, price: this.newPrice });
      this.newOrder = "";
      this.newPrice = "";
    },
    removeOrderAtIndex: function(index) {
      this.orders.splice(index, 1);
    },
  },
};
</script>

<style>
table {
  background: lightyellow;
}
</style>
