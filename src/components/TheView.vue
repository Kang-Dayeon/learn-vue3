<template>
  <main>
    <div class="container py-4">
      <!-- <my-button class="my-button" id="my-button" @click="sayHello"></my-button> -->
      <my-button class="my-button" id="my-button" @click="sayHello"></my-button>
      <label-input label="이름" data-id="id입니다"></label-input>
      <hr/>
      <fancy-button>Click!<span style="color: red;">@@@</span></fancy-button>
      <fancy-button></fancy-button>
      <hr/>
      <app-card>
        <!-- slot을 동적으로 변경 할 수 있다. -->
        <template #[slotArgs]>제목입니다</template>
        <!-- <template v-slot>내용입니다</template> -->
        <!-- 기본적으로 자식 컴포넌트의 데이터에는 접근 할 수 없지만 Scoped Slot를 사용하면 가능하다 -->
        <template #default="{childMessage}">
          암시적으로 Default 슬롯입니다.
          <br/>
          {{ message }}
          <br/>
          {{ childMessage }}
        </template>
        <template #footer>푸터입니다</template>
      </app-card>
      <hr/>
      <app-card>
        <template #default>body</template>
      </app-card>
    </div>
  </main>
</template>

<script>
import { ref } from 'vue';
import AppCard from './AppCard.vue';
import FancyButton from './FancyButton.vue';
import LabelInput from './LabelInput.vue';
import MyButton from './MyButton.vue';

export default {
  components: {
    MyButton,
    LabelInput,
    FancyButton,
    AppCard,
  },
  setup() {
    const sayHello = () => {
      alert("안녕하세요");
    };
    const slotArgs = ref('header');
    const message = ref('부모 컴포넌트 메세지');
    return {
      sayHello,
      slotArgs,
      message,
    }
  }
}
</script>

<style lang="scss" scoped>
</style>