<template>
  <div class="show-list">
    <div class="show-list__controls">
      <h2>{{ list.title }}</h2>
      <my-button @click="changeSorted" v-if="list.isSelected">
        {{ isSorted ? "Перемешать" : "Сортировать" }}
      </my-button>
    </div>
    <div class="show-list__container">
      <div class="show-list__item" v-for="item in list.items" v-if="isSorted">
        <show-item
          v-for="block in item.count"
          :item="item"
          v-if="item.isSelected"
          @item-deleted="onItemDeleted"
        />
      </div>
      <div class="show-list__item" v-else>
        <show-item
          v-for="item in splitArray(list.items)"
          :item="item"
          @item-deleted="onItemDeleted"
        />
      </div>
    </div>
  </div>
</template>

<script>
import ShowItem from "@/components/ShowItem.vue";
import MyButton from "@/components/UI/MyButton.vue";

export default {
  name: "show-list",
  components: { MyButton, ShowItem },
  props: {
    list: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      isSorted: false,
    };
  },
  methods: {
    onItemDeleted(item) {
      const foundedItem = this.list.items.find((it) => it.title === item.title);

      foundedItem.count -= 1;
    },

    changeSorted() {
      this.isSorted = !this.isSorted;
    },

    splitArray(arr) {
      if (this.isSorted) return;

      const result = [];
      let newArr = JSON.parse(JSON.stringify(arr));
      const count = newArr.reduce((acc, item) => {
        if (item.isSelected) {
          acc += item.count;
        }

        return acc;
      }, 0);

      for (let i = 0; i < count; i++) {
        const randomItem = Math.floor(Math.random() * newArr.length);

        if (!newArr[randomItem].isSelected) {
          i -= 1;
          continue;
        }

        if (newArr[randomItem].count === 0) {
          newArr = newArr.filter(
            (item) => item.title !== newArr[randomItem].title
          );

          i -= 1;

          continue;
        }

        newArr[randomItem].count -= 1;
        result.push(newArr[randomItem]);
      }

      return result;
    },
  },
};
</script>

<style scoped>
.show-list {
  display: flex;
  flex-direction: column;
  gap: 5px;
  width: 100%;
  border: 2px solid black;
  padding: 5px;
}

.show-list__controls {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
}

.show-list h2 {
  font-size: 14px;
}

.show-list__container {
  display: flex;
  flex-direction: column;
  gap: 5px;
  width: 100%;
  height: max-content;
}

.show-list__item {
  display: flex;
  width: 100%;
  height: max-content;
  gap: 2px;
  flex-wrap: wrap;
  position: relative;
}
</style>
