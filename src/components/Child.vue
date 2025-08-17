<template>
  <div class="card">
    <div class="card-header">Child Component</div>
    <div class="card-body">
      <deep-child></deep-child>
    </div>
  </div>
</template>

<script>
import DeepChild from './DeepChild.vue';

export default {
  components: {
    DeepChild,
  },
  setup () {
    return {}
  }
}
</script>

<style lang="scss" scoped>
</style>