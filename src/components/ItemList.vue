<template>
  <ul class="items">
    <li class="item" v-for="item in items" v-bind:key="item.id">
      <img src="https://dummyimage.com/200.png/09f/fff" alt="dummy">
      <div class="title">{{ item.title }}</div>
      <div class="price">{{ item.price }}円</div>
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    items: Array,
  },
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
