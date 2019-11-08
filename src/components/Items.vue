<template>
  <ul class="items">
    <li class="item" v-for="item in sortedItems">
      <img src="https://dummyimage.com/200.png/09f/fff" alt="dummy">
      <div class="title">{{ item.title }}</div>
      <div class="price">{{ item.price }}円</div>
    </li>
  </ul>
</template>

<script>
export default {
  computed: {
    sortedItems: function() {
      switch (this.componentOrder) {
        case "low":
          return [...this.items].sort((a, b) => a.price - b.price);
        case "high":
          return [...this.items].sort((a, b) => b.price - a.price);
        default:
          return [...this.items];
      }
    }
  },
  props: {
    componentOrder: String
  },
  data: function() {
    return {
      items: this.createItems(9)
    };
  },
  methods: {
    createItem: function() {
      return {
        title: "title" + Math.round(Math.random() * 100),
        price: Math.round(Math.random() * 100) * 100
      };
    },
    createItems: function(i) {
      return Array.apply(null, Array(i)).map(() => this.createItem());
    },
    loadItems: function() {
      this.items.push(...this.createItems(5));
    }
  }
};
</script>

<style>
.items {
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-start;
  padding: 0;
}

.item {
  list-style: none;
  text-align: center;
  width: 15%;
  margin: 2em 2.5%;
}

.item img {
  width: 100%;
}

.price,
.title {
  font-size: 1.4em;
}
</style>
