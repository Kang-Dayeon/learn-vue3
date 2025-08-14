<template>
  <main>
    <div class="container py-4">
      <!-- <my-button class="my-button" id="my-button" @click="sayHello"></my-button> -->
      <my-button class="my-button" id="my-button" @click="sayHello"></my-button>
      <label-input label="이름" data-id="id입니다"></label-input>
    </div>
  </main>
</template>

<script>
import LabelInput from './LabelInput.vue';
import MyButton from './MyButton.vue';

export default {
  components: {
    MyButton,
    LabelInput,
  },
  setup() {
    const sayHello = () => {
      alert("안녕하세요")
    }
    return {
      sayHello,
    }
  }
}
</script>

<style lang="scss" scoped>
</style>