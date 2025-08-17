<template>
  <div class="container py-4">
    <input ref="inputRef" type="text" value="hello world" />
    <p id="message">{{ messgae }}</p>
    <hr/>
    <button @click="visible = !visible">Toggle Child</button>
    <lifecycle-child v-if="visible"></lifecycle-child>
  </div>
</template>

<script>
import { onBeforeMount, onBeforeUpdate, onMounted, onUpdated, ref } from 'vue';
import LifecycleChild from './LifecycleChild.vue';
export default {
  components: {
    LifecycleChild,
  },
  setup () {
    const messgae = ref('');
    const inputRef = ref(null);
    const visible = ref(false);
    console.log('setup');

    // vue3에서는 아래의 라이프 사이클 훅을 setup함수 내에서 사용할 수 있다.

    // 📍 Mouting
    // mount는 dom에 컴포넌트를 삽입하는 단계이다
    onBeforeMount(() => {
      // 컴포넌트가 마운트되기 직전에 호출
      // 대부분 사용을 권장하지 않음
      console.log('onBeforMount');
    });
    // ✅ 이 사이에서 자식 컴포넌트를 생성하여 완료되면 부모의 onMounted를 실행한다.
    onMounted(() => {
      // 컴포넌트가 마운트된 후에 호출
      // dom에 접근할 수 있다
      console.log('onMounted', inputRef.value.value)
    });

    // 📍 Updating
    //  반응형 상태 변경으로 컴포넌트의 dom트리가 업데이트된 후 호출되는 콜백을 등록
    onBeforeUpdate(() => {
      console.log('onBeforeUpdate', messgae.value);
      console.log(
        'DOM Content: ',
        document.querySelector('#message').textContent
      );
    });
    onUpdated(() => {
      console.log('onUpdated', messgae.value);
      console.log(
        'DOM Content: ',
        document.querySelector('#message').textContent
      );
    });

    return {
      inputRef,
      messgae,
      visible,
    }
  },
  // 아래는 vue2문법
  // 📍 Creating
  // 컴포넌트 초기화 단계
  // beforCreate와 created는 vue3에서는 setup으로 대체 가능
  data: () => ({
    dataMessage: 'data messgae',
  }),
  beforeCreate() {
    // componet가 초기화 될 때 사용되는 훅
    console.log('beforCreate');
    // 데이터 옵션을 처리하기 전이기 때문에 접근 불가
    console.log(this.dataMessage);
  },
  created() {
    // 컴포넌트 인스턴스가 초기화를 완료한 후 호출되는 훅이다.
    console.log('created');
    // 데이터 옵션을 처리한 후 이기 때문에 접근 가능
    console.log(this.dataMessage);
  },
}
</script>

<style lang="scss" scoped>
</style>