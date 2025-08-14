<template>
  <!-- 부모 컴포넌트의 class나 style은 병합된다 -->
  <label         
    class="child-class"
    style="border: 1px solid black;"
    id="child-id"
  >
    {{ label }}
    <input 
      v-model="value"
      type="text" 
    />

        <!-- :value="modelValue" 
    @input="event => $emit('update:modelValue', event.target.value)" -->

    <!-- v-model은 아래의 기능과 같음 (양반향 바인딩을 할 수 있음)-->
    <!-- <input 
      :value="username"
      @input="event => (username = event.target.value)"
      type="text"
    /> -->
  </label>
</template>

<script>
import { computed } from 'vue';

export default {
  props: ['modelValue', 'label'],
  emits: ['update:modelValue'],
  setup (props, {emit}) {
    const value = computed({
      get() {
        return props.modelValue;
      },
      set(value) {
        emit('update:modelValue', value);
      }
    })
    return { 
      value,

    }
  }
}
</script>

<style lang="scss" scoped>
</style>