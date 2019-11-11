<template>
  <div id="app">
    <order-select v-model="order"></order-select>
    <item-list v-bind:items="sortedItems"></item-list>
    <show-more-button v-on:click="loadItems"></show-more-button>
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
    this.addItems(9);
  },

  methods: {
    createItem() {
      return {
        id: Math.random(),
        title: "title" + Math.round(Math.random() * 100),
        price: Math.round(Math.random() * 100) * 100
      };
    },

    addItems(count) {
      const newItems = [...Array(count)].map(() => this.createItem());
      this.items.push(...newItems);
    },

    loadItems() {
      this.addItems(5);
    }
  }
};
</script>
