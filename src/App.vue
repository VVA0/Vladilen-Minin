<template>
  <div class="app">
    <PlainBlock />
  </div>
</template>

<script>
import PlainBlock from "./components/PlainBlock/Index.vue";

export default {
  name: "App",
  components: { PlainBlock },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;500&display=swap");

body {
  font-family: Inter, Roboto, Oxygen, Fira Sans, Helvetica Neue, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-size: 16px;
  color: #2c3e50;
  background: #2c3e50;
}
.app {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
