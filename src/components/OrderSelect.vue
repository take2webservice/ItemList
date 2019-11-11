<template>
  <div>
    <select class="order" name="order" v-model="innerComponentOrder">
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
    componentOrder: String
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
    innerComponentOrder: {
      get() {
        return this.componentOrder;
      },
      set(value) {
        this.$emit("update-order", value);
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
