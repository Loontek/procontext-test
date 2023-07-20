<template>
  <div
    class="show-item"
    :style="{ 'background-color': item.color }"
    @click="deleteItem"
  ></div>
</template>

<script>
export default {
  name: "show-item",
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
  methods: {
    deleteItem() {
      this.$emit("item-deleted", this.item);
    },
  },
};
</script>

<style scoped>
.show-item {
  width: 10px;
  height: 10px;
  background: red;
}
</style>
