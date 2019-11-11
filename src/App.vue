<template>
  <div id="app">
    <order-select v-bind:component-order="order" v-on:update-order="updateOrder"></order-select>
    <item-list ref="items" v-bind:component-order="order"></item-list>
    <show-more-button v-on:show-more="loadItems"></show-more-button>
  </div>
</template>

<script>
import ItemList from "./components/ItemList";
import ShowMoreButton from "./components/ShowMoreButton";
import OrderSelect from "./components/OrderSelect";

export default {
  name: "App",
  data(){
    return{
      order: "normal"
    }
  },
  components: {
    "item-list": ItemList,
    "show-more-button": ShowMoreButton,
    "order-select": OrderSelect
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
