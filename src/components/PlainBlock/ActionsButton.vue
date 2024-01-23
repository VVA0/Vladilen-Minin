<template>
  <button @click="clickButton" :disabled="disabled" class="btn" :class="{ 'out-line': outlined }">
    {{ text }}
  </button>
</template>

<script>
export default {
  name: "ActionsButton",
  props: ["text", "disabled", "outlined"],
  methods: {
    clickButton() {
      this.$emit("click");
    },
  },
};
</script>

<style scoped lang="scss">
$green: rgb(68, 163, 102);
.btn {
  border: 0;
  background-color: $green;
  border-radius: 20px;
  padding: 5px 20px;
  color: white;
  &.out-line {
    background-color: white;
    color: $green;
    border: 1px solid $green;
  }
  &:disabled {
    background-color: #bbbbbb;
    color: #777777;
    opacity: 0.3;
  }
}
</style>
