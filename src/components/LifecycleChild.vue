<template>
  <div class="card">
    <div class="card-body">Lifecycle Child</div>
    <input id="input" type="text" />
  </div>
</template>

<script>
import { onBeforeMount, onBeforeUnmount, onMounted, onUnmounted } from 'vue';

export default {
  setup () {
    console.log('[Child] setup');
    onBeforeMount(() => {
      console.log('[Child] onBeforeMount');
    })
    onMounted(() => {
      console.log('[Child] onMounted');
    })

    // 📍 Destruction
    // 소멸단계
    onBeforeUnmount(() => {
      // 컴포넌트 마운트가 해제되기 직전 호출
      console.log('[Child] onBeforeUnmount');
      // 돔에 마운트를 해제되지 직전이기 때문에 돔을 가져올 수 있다
      console.log(document.querySelector('#input'));
    }),
    onUnmounted(() => {
      // 컴포넌트가 마운트 해제된 후 호출
      console.log('[Child] onUnmounted');
      // 돔에 마운트를 해제 한 후이기 때문에 돔을 가져올 수 없다
      console.log(document.querySelector('#input'));
    })
    return {}
  }
}
</script>

<style lang="scss" scoped>

</style>