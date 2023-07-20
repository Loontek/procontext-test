<template>
  <button type="button"><slot></slot></button>
</template>

<script>
export default {
  name: "my-button",
};
</script>

<style scoped>
button {
  padding: 3px 8px;
  background-color: #1ba3f2;
  color: white;
  border: none;
  outline: none;
  font-size: 10px;
  border-radius: 5px;
  cursor: pointer;
}
</style>
