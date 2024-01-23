<template>
  <div class="card">
    <h2 class="title">План по изучению vue.js</h2>
    <p class="paragraph">{{ selectedText }}</p>
    <div class="titles">
      <ItemList
        v-for="(item, index) in list"
        :key="index"
        :index="index"
        :title="item.title"
        :selected="index === indexList"
        :is-past-item="index < indexList"
      />
    </div>
    <Actions @changeIndexList="setIndexList" :list-length="list.length" :index-list="indexList" />
  </div>
</template>

<script>
import ItemList from "./ItemList.vue";
import Actions from "./Actions.vue";
import ActionsButton from "./ActionsButton.vue";

export default {
  name: "App",
  components: {
    ItemList,
    Actions,
    ActionsButton,
  },
  data() {
    return {
      indexList: 0,
      list: [
        {
          title: "Основы",
          text: "В блоке вы познакомитесь со всеми основами Vue.js на практике. На протяжении блока мы напишем реактивное приложение, в процессе разработки которого разберем вся базу фреймворка.",
        },
        {
          title: "Компоненты",
          text: "Один из самых важных блоков в курсе, где вы узнаете все о компонентах. В блоке мы напишем 2 разных приложения и создадим более 5 различных UI компонентов как в реальной разработке. Блок расскажет про абсолютно все составляющие, которые есть в компонентах: взаимодействие, slots, асинхронные и динамические компоненты и тонна примеров.",
        },
        {
          title: "Роутер",
          text: "В данном блоке вы узнаете все о том, как работает мультиязычность во Vue. Мы создадим миниклон Gmail в данном блоке, где вы на практике увидите как работать с динамическим роутером.",
        },
        {
          title: "Vuex",
          text: "В блоке вы узнаете абсолютно все про Vuex. Вы узнаете как работать с данными, какие есть лучшие практики по их программированию и структурированию. Все на практике.",
        },
        {
          title: "Composition",
          text: "Одним из наиболее важных обновлений в Vue 3 является появление альтернативного синтаксиса Composition API. В этом блоке вы узнаете все, чтобы полностью пользоваться данными синтаксисом на практических примерах. Помимо этого вы узнаете как работать совместно с Vue Router и Vuex.",
        },
      ],
    };
  },
  computed: {
    selectedText() {
      return this.list[this.indexList].text; // берем объект из переменной лист по индексу и достаем текст
    },
  },
  methods: {
    setIndexList(value) {
      this.indexList = value;
    },
  },
};
</script>

<style scoped lang="scss">
.titles {
  display: flex;
  gap: 30px;
  justify-content: space-between;
  width: 100%;
}
.card {
  background-color: white;
  border-radius: 5px;
  padding: 10px;
  box-shadow: 4px 4px 8px 0px rgba(34, 60, 80, 0.2);
  max-width: 800px;
}
</style>
