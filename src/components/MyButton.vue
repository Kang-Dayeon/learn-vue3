<template>
  <div class="p-3 bg-danger">
    <!-- v-bind로 $attrs 를 바인딩 할 수 있다 -->
    <button 
      type="button" 
      class="btn btn-primary"
      v-bind="$attrs"
    >
      My Button
    </button>
  </div>
</template>

<script>
export default {
  // 속성 상속을 막는 설정
  inheritAttrs: false,
  setup (props, context) {
    // context.attrs는 부모에서 상속한 class나 event 속성을 가지고 있음
    console.log(context.attrs)
    console.log(context.attrs.class)
    console.log(context.attrs.id)
    console.log(context.attrs.onClick)
    return {}
  }
}
</script>

<style lang="scss" scoped>
</style>