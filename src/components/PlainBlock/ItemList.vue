<template>
  <div class="item-list">
    <div
      :class="{ 'item-list__selected': selected, 'item-list__past': isPastItem }"
      class="item-list__index"
    >
      {{ index + 1 }}
    </div>
    {{ title }}
  </div>
</template>

<script>
export default {
  name: "ItemList",
  props: ["title", "index", "selected", "isPastItem"],
};
</script>

<style scoped lang="scss">
.item-list {
  display: flex;
  align-items: center;
  &__index {
    padding: 10px;
    width: 10px;
    height: 10px;
    border-radius: 50%;
    background-color: rgb(213, 211, 211);
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 12px;
    margin-right: 5px;
  }
  &__selected,
  &__past {
    background-color: rgb(68, 163, 102);
  }
  &__selected {
    color: white;
  }
}
</style>
