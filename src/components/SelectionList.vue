<template>
  <div
    class="selection-list"
    :class="{
      'selection-list_show': isShow,
    }"
  >
    <div class="selection-list__controls">
      <button @click="showContent"></button>
      <label class="selection-list__label">
        <input
          class="selection-list__checkbox"
          type="checkbox"
          v-model="list.isSelected"
          @change="changeSelected"
        />
      </label>
      <h2>{{ list.title }}</h2>
    </div>
    <div class="selection-list__content" v-if="isShow">
      <selection-item
        v-for="item in list.items"
        :item="item"
        @item-selected="onItemSelected"
      />
    </div>
  </div>
</template>

<script>
import SelectionItem from "@/components/SelectionItem.vue";

export default {
  name: "selection-list",
  components: { SelectionItem },
  props: {
    list: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      isShow: false,
    };
  },
  methods: {
    showContent() {
      this.isShow = !this.isShow;
    },
    changeSelected(e) {
      this.list.items.forEach((item) => {
        item.isSelected = this.list.isSelected;
      });
    },
    onItemSelected() {
      const item = this.list.items.find((item) => item.isSelected);

      if (!item) {
        this.list.isSelected = false;
      }

      if (item) {
        this.list.isSelected = true;
      }
    },
  },
};
</script>

<style scoped>
.selection-list__controls {
  display: flex;
  align-items: center;
  gap: 10px;
}

.selection-list__content {
  padding: 10px 45px;
  display: flex;
  flex-direction: column;
  gap: 5px;
}

.selection-list button {
  width: 10px;
  height: 10px;
  border: none;
  border-bottom: 2px solid black;
  border-left: 2px solid black;
  border-radius: 2px;
  transform: rotate(225deg);
  background: transparent;
  cursor: pointer;
  transition: tranform 0.2s ease;
}

.selection-list_show button {
  transform: rotate(-45deg) translate(2px, -2px);
}

.selection-list h2 {
  font-size: 14px;
}

.selection-list__label {
  width: 15px;
  height: 15px;
  display: flex;
  justify-content: center;
  border: 1px solid black;
  align-items: center;
  cursor: pointer;
}

.selection-list__label:has(.selection-list__checkbox:checked):before {
  content: "";
  display: block;
  width: 5px;
  height: 5px;
  background: black;
}

.selection-list__checkbox {
  display: none;
}
</style>
