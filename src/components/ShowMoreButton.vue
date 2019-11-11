<template>
  <div class="btn_wrap">
    <button class="more" v-on:click="onClick">さらに読み込む(c)</button>
  </div>
</template>

<script>
export default {
  methods: {
    onClick() {
      this.$emit("click");
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
