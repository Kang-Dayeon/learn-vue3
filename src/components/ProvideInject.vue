<template>
  <div class="container py-4">
    <div class="card">
      <div class="card-header">ProvideInject Component</div>
        <div class="card-body">
          <button @click="count++">Click</button>
          <p>appMessage : {{ appMessage }}</p>
          <child></child>    
        </div>
    </div>
  </div>
</template>

<script>
import { inject, provide, readonly, ref } from 'vue';
import Child from './Child.vue';
export default {
  components: {
    Child,
  },
  setup () {
    const staticMessage = 'static message';
    const message = ref('message');
    const updateMessage = (appenMessage) => {
      message.value = message.value + appenMessage;
    }
    const count = ref(10);

    // provide('staticMessage', staticMessage);
    provide('message', { message: readonly(message), updateMessage });
    provide('count', count);

    const appMessage = inject('app-message');

    return {
      count,
      appMessage,
    }
  },
  mounted() {
    console.log(this.msg);
  }
}
</script>

<style lang="scss" scoped>

</style>