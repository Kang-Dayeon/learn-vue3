<template>
  <div class="container py-4">
    {{ msg }}
    <br/>
    {{ message }}
    <input v-model="message" type="text">
    <button @click="sayHello">Click!</button>
    <post-item
      type="news"
      title="제목"
      contents="내용"
      :is-like="true"
    ></post-item>
    <hr/>
    <TemplateRefsChild ref="child"></TemplateRefsChild>
    <template v-if="child">{{ child.message }}</template>
    <hr>
    <my-button class="parent-class"></my-button>
  </div>
</template>

<!-- 이 전까지 사용했던 setup(){}이 태그에 컴파일됨 -->
<script setup>
import axios from 'axios';
import { ref } from 'vue'
import PostItem from './setup/PostItem.vue'
import TemplateRefsChild from './setup/TemplateRefsChild.vue'
import MyButton from './setup/MyButton.vue';

const msg = 'hello'
const message = ref('')
const sayHello = () => {
  alert('hello world!')
}

const child = ref(null)

defineExpose({
  msg
})

const res = await axios('https://dummy.restapiexample.com/api/v1/employees')
console.log(res)
</script>

<style lang="scss" scoped>
</style>