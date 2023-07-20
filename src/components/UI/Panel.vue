<template>
  <div class="panel">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "panel",
};
</script>

<style scoped>
.panel {
  width: 40%;
  min-height: 200px;
  border: 2px solid black;
  padding: 15px;
  display: flex;
  flex-direction: column;
  gap: 10px;
}
</style>
