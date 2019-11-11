<template>
  <div>
    <select class="order" name="order" v-model="order">
      <option
        v-for="option in orderOptions"
        v-bind:value="option.value"
        v-bind:key="option.value"
      >{{ option.text }}</option>
    </select>
  </div>
</template>

<script>
export default {
  props: {
    value: String
  },

  data() {
    return {
      orderOptions: [
        { text: "読み込み順", value: "normal" },
        { text: "価格が安い順", value: "low" },
        { text: "価格が高い順", value: "high" }
      ]
    };
  },

  computed: {
    order: {
      get() {
        return this.value;
      },
      set(value) {
        this.$emit("input", value);
      }
    }
  }
};
</script>

<style>
.order {
  font-size: 1.3em;
}
</style>
