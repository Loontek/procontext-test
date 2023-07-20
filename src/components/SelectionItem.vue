<template>
  <div class="selection-item">
    <div class="selection-item__content">
      <label class="selection-item__label">
        <input
          class="selection-item__checkbox"
          v-model="item.isSelected"
          @change="changeSelected"
          type="checkbox"
        />
      </label>
      <h3>{{ item.title }}</h3>
    </div>
    <div class="selection-item__content">
      <input type="number" v-model="item.count" min="0" max="99" />
      <input type="color" v-model="item.color" />
    </div>
  </div>
</template>

<script>
export default {
  name: "selection-item",
  props: {
    item: {
      type: Object,
      required: true,
    },
    isListSelected: Boolean,
  },
  data() {
    return {};
  },
  methods: {
    changeSelected(e) {
      this.$emit("item-selected", this.item);
    },
  },
};
</script>

<style scoped>
.selection-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 10px;
}

.selection-item h3 {
  font-size: 12px;
}

.selection-item input[type="color"] {
  width: 15px;
  height: 15px;
  padding: 0;
  border: none;
  outline: none;
}

.selection-item input[type="number"] {
  width: 15px;
  height: 15px;
  padding: 0;
  border: none;
  outline: none;
}

.selection-item input[type="number"]::-webkit-outer-spin-button,
.selection-item input[type="number"]::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

.selection-item__content {
  display: flex;
  align-items: center;
  gap: 10px;
}

.selection-item input[type="color"]::-webkit-color-swatch-wrapper {
  padding: 0;
}

.selection-item__label {
  width: 15px;
  height: 15px;
  display: flex;
  justify-content: center;
  border: 1px solid black;
  align-items: center;
  cursor: pointer;
}

.selection-item__label:has(.selection-item__checkbox:checked):before {
  content: "";
  display: block;
  width: 8px;
  height: 4px;
  border-bottom: 1px solid black;
  border-left: 1px solid black;
  transform: rotate(-45deg) translate(1px, -1px);
}

.selection-item__checkbox {
  display: none;
}
</style>
