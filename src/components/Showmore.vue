<template>
  <div class="btn_wrap">
    <button class="more" v-on:click="loadItems">さらに読み込む(c)</button>
  </div>
</template>

<script>
export default {
  methods: {
    loadItems: function() {
      //eventhub.$emit('show-more')
      this.$emit("show-more");
    }
  }
};
</script>

<style>
.more {
  background-color: #09f;
  color: white;
  font-size: 2em;
  display: inline-block;
  padding: 0.5em 3em;
}

.btn_wrap {
  text-align: center;
}
</style>
