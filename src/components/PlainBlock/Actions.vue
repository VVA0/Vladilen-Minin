<template>
  <div @click="clickButton" class="btns">
    <ActionsButton
      v-show="!isResetButtonShow"
      @click="backClick"
      :disabled="isDisabledBackButton"
      text="Назад"
      :outlined="true"
    />
    <ActionsButton v-show="isFrontButtonShow" @click="frontClick" text="Вперед" />
    <ActionsButton v-show="isEndButtonShow" @click="changeIsResetButtonShow" text="Закончить" />
    <ActionsButton
      v-show="isResetButtonShow"
      @click="resetForm"
      text="Начать заново"
      :outlined="true"
    />

    <!-- <button
      v-show="!isResetButtonShow"
      class="btn"
      @click="backClick"
      :disabled="isDisabledBackButton"
    >
      Назад
    </button>
    <button v-show="isFrontButtonShow" class="btn" @click="frontClick">Вперед</button>
    <button v-show="isEndButtonShow" class="btn" @click="changeIsResetButtonShow">Закончить</button>
    <button v-show="isResetButtonShow" class="btn" @click="resetForm">Начать заново</button> -->
  </div>
</template>

<script>
import ActionsButton from "./ActionsButton.vue";

export default {
  name: "Actions",
  components: { ActionsButton },
  props: ["indexList", "listLength"],
  data() {
    return {
      isResetButtonShow: false,
    };
  },
  computed: {
    isDisabledBackButton() {
      // не является ли индекс первым?
      return !this.indexListComputed;
      // if (indexList > 0) {
      //   return false;
      // }
      // return true;
    },
    isFrontButtonShow() {
      return !this.isLastIndex && !this.isResetButtonShow; // пишу computed свойство для отображения кнопки вперед
    },
    isEndButtonShow() {
      return this.isLastIndex && !this.isResetButtonShow; // пишу проверку на то, показывать ли кнопку закончить
    },
    indexListComputed: {
      get() {
        return this.indexList;
      },
      set(value) {
        this.$emit("changeIndexList", value);
      },
    },
    isLastIndex() {
      return this.indexList === this.listLength - 1; // является ли последний индекс активным?
    },
  },
  methods: {
    backClick() {
      this.indexListComputed -= 1; // перемещаю активный индекс на 1 назад
    },
    frontClick() {
      this.indexListComputed += 1; // перемещаю активный индекс на 1 вперед
    },
    changeIsResetButtonShow() {
      this.isResetButtonShow = !this.isResetButtonShow;
    },
    resetForm() {
      this.indexListComputed = 0;
      this.isResetButtonShow = false;
    },
    clickButton() {
      this.$emit("click");
    },
  },
};
</script>

<style scoped lang="scss">
.btns {
  display: flex;
  gap: 10px;
  padding: 10px 0px;
}
</style>
