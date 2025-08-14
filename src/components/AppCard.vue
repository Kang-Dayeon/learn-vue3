<template>
  <div class="card">
    <!-- haader슬롯이 있는 곳에만 사용할 수 있음 -->
    <div v-if="$slots.header" class="card-header">
      <slot name="header">#Header</slot>
    </div>
    <div v-if="$slots.default" class="card-body">
      <!-- Scoped Slot으로 데이터 전송 -> props랑 비슷한 기능 -->
      <slot :childMessage="childMessage">#Body</slot>
    </div>
    <div v-if="hasFooter" class="card-footer text-body-secondary">
      <slot name="footer">#Footer</slot>
    </div>
  </div>
</template>

<script>
import { computed, ref } from 'vue';

export default {
  setup (props, { slots }) {
    const childMessage = ref('자식 컴포넌트 메세지');
    const hasFooter = computed(() => !!slots.footer);
    return {
      childMessage,
      hasFooter,
    }
  }
}
</script>

<style lang="scss" scoped>

</style>