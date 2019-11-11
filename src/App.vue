<template>
  <div id="app">
    <order-select v-bind:component-order="order" v-on:update-order="updateOrder"></order-select>
    <item-list v-bind:items="sortedItems"></item-list>
    <show-more-button v-on:show-more="loadItems"></show-more-button>
  </div>
</template>

<script>
import ItemList from "./components/ItemList";
import ShowMoreButton from "./components/ShowMoreButton";
import OrderSelect from "./components/OrderSelect";

export default {
  name: "App",
  components: {
    "item-list": ItemList,
    "show-more-button": ShowMoreButton,
    "order-select": OrderSelect
  },

  data(){
    return{
      items: [],
      order: "normal"
    }
  },

  computed: {
    sortedItems() {
      switch (this.order) {
        case "low":
          return [...this.items].sort((a, b) => a.price - b.price);
        case "high":
          return [...this.items].sort((a, b) => b.price - a.price);
        default:
          return [...this.items];
      }
    }
  },

  created() {
    this.loadItems();
  }
  ,
  methods: {
    updateOrder(order) {
      this.order = order;
    },

    createItem() {
      return {
        id: Math.random(),
        title: "title" + Math.round(Math.random() * 100),
        price: Math.round(Math.random() * 100) * 100
      };
    },

    createItems(i) {
      return Array.apply(null, Array(i)).map(() => this.createItem());
    },

    loadItems() {
      this.items.push(...this.createItems(5));
    }
  }
};
</script>
