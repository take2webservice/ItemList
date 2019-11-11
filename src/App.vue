<template>
  <div id="app">
    <order-component v-bind:component-order="order" v-on:update-order="updateOrder"></order-component>
    <items-component ref="items" v-bind:component-order="order"></items-component>
    <showmore-component v-on:show-more="loadItems"></showmore-component>
  </div>
</template>

<script>
import Items from "./components/Items";
import Order from "./components/Order";
import Showmore from "./components/Showmore";

export default {
  name: "App",
  data(){
    return{
      order: "normal"
    }
  },
  components: {
    "items-component": Items,
    "showmore-component": Showmore,
    "order-component": Order
  },
  methods: {
    loadItems() {
      this.$refs.items.loadItems();
    },
    updateOrder(order) {
      this.order = order;
    }
  }
};
</script>
