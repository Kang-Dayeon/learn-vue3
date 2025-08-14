<!-- ✅ 자식에서 부모로 데이터 전달 또는 트리거 목적으로 이벤트를 내보내는 방법 -->
<!-- ▸ emit을 사용하면 자식에서 부모로 이벤트 전달 가능 -->
<template>
  <div class="row g-3">
    <div class="col col-2">
      <select 
      v-model="type" 
      class="form-select" 
      aria-label="Default select example">
        <option selected></option>
        <option value="news">뉴스</option>
        <option value="notice">공지사항</option>
      </select>
    </div>
    <div class="col col-8">
      <input v-model="title" type="text" class="form-control">
    </div>
    <div class="col col-2 d-grid">
      <button class="btn btn-primary" @click="createPost">추가</button>
    </div>
    <!-- 직접 이벤트 발송하기 -->
    <!-- <button class="btn btn-primary" @click="$emit('createPost', 1, 2, 3, 'ddd')">button</button> -->
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
 // 💡 vue3에서는 emits 옵션을 사용하여 이벤트를 선언할 수 있다.
 // ❗️이벤트는 왠만하면 emits선언하자!

  // ■ emits 문자열 배열 서언 방식
  // emits: ['createPost'];
  emits: {
    // ■ emits 객체문법 선언 방식
    // 객체 문법으로 선언할 경우 validation로직을 추가할 수 있다. validation이 없다면 null로 설정.
    createPost: (newPost) => {
      if(!newPost.type) {
        return false;
      } else if (!newPost.title) {
        return false;
      }
      return true;
    }
  },
  setup (props, {emit}) {
    const type = ref('news');
    const title = ref('');
    const createPost = () => {
      const newPost = {
        type: type.value,
        title: title.value,
      }
      emit('createPost', newPost);
      type.value = 'news';
      title.value = '';
    };

    return {createPost, title, type}
  }
}
</script>

<style lang="scss" scoped></style>