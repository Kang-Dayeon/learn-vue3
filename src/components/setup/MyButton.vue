<template>
  <div class="p-3 bg-danger">
    <!-- v-bind로 $attrs 를 바인딩 할 수 있다 -->
    <button 
      type="button" 
      class="btn btn-primary"
      @click="sayHello"
    >
    <!-- v-bind="$attrs" -->
      My Button
    </button>
  </div>
</template>

<script>
export default {
  // 속성 상속을 막는 설정
  inheritAttrs: false,
}
</script>

<script setup></script>
<style lang="scss" scoped>
</style>