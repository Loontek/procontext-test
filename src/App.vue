<template>
  <div class="app">
    <panel>
      <selection-list v-for="list in lists" :list="list" />
    </panel>
    <panel>
      <show-list v-for="list in lists" :list="list" />
    </panel>
  </div>
</template>

<script>
import SelectionList from "@/components/SelectionList.vue";
import ShowList from "@/components/ShowList.vue";
import Panel from "@/components/UI/Panel.vue";

export default {
  components: { Panel, ShowList, SelectionList },
  data() {
    return {
      lists: [
        {
          title: "List 1",
          isSelected: false,
          items: [
            { title: "Item 1", count: 10, color: "#FF0000", isSelected: false },
            { title: "Item 2", count: 16, color: "#FFFF00", isSelected: false },
            { title: "Item 3", count: 40, color: "#00FF00", isSelected: false },
            { title: "Item 4", count: 0, color: "#0000FF", isSelected: false },
          ],
        },
        {
          title: "List 2",
          items: [
            { title: "Item 1", count: 10, color: "#FF0000", isSelected: false },
            { title: "Item 2", count: 16, color: "#FFFF00", isSelected: false },
            { title: "Item 3", count: 40, color: "#00FF00", isSelected: false },
            { title: "Item 4", count: 0, color: "#0000FF", isSelected: false },
            { title: "Item 5", count: 20, color: "#F4CA16", isSelected: false },
            { title: "Item 6", count: 12, color: "#CC397B", isSelected: false },
          ],
        },
        {
          title: "List 3",
          items: [
            { title: "Item 1", count: 20, color: "#FF0000", isSelected: false },
            { title: "Item 2", count: 36, color: "#FFFF00", isSelected: false },
            { title: "Item 3", count: 10, color: "#00FF00", isSelected: false },
            { title: "Item 4", count: 15, color: "#0000FF", isSelected: false },
            { title: "Item 5", count: 22, color: "#F4CA16", isSelected: false },
            { title: "Item 6", count: 2, color: "#CC397B", isSelected: false },
            { title: "Item 7", count: 2, color: "#20B2AA", isSelected: false },
            { title: "Item 8", count: 2, color: "#004242", isSelected: false },
          ],
        },
        {
          title: "List 4",
          items: [
            { title: "Item 1", count: 20, color: "#FF0000", isSelected: false },
            { title: "Item 2", count: 36, color: "#FFFF00", isSelected: false },
            { title: "Item 3", count: 10, color: "#00FF00", isSelected: false },
            { title: "Item 4", count: 15, color: "#0000FF", isSelected: false },
            { title: "Item 5", count: 22, color: "#F4CA16", isSelected: false },
          ],
        },
        {
          title: "List 5",
          items: [
            { title: "Item 1", count: 20, color: "#FF0000", isSelected: false },
            { title: "Item 2", count: 36, color: "#FFFF00", isSelected: false },
            { title: "Item 3", count: 10, color: "#00FF00", isSelected: false },
            { title: "Item 4", count: 15, color: "#0000FF", isSelected: false },
            { title: "Item 5", count: 22, color: "#F4CA16", isSelected: false },
            { title: "Item 6", count: 5, color: "#CC397B", isSelected: false },
            { title: "Item 7", count: 24, color: "#20B2AA", isSelected: false },
            { title: "Item 8", count: 13, color: "#A0E6FF", isSelected: false },
            { title: "Item 9", count: 45, color: "#FCE883", isSelected: false },
            {
              title: "Item 10",
              count: 28,
              color: "#004242",
              isSelected: false,
            },
          ],
        },
      ],
      isSorted: false,
    };
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "Arial", sans-serif;
}

.app {
  min-height: 100vh;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 30px;
  padding: 50px;
}
</style>
