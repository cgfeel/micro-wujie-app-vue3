<template>
  <div class="about">
    <h1>This is an about page</h1>
    <p>
      url: {{ url }}
    </p>
    <p>
      <a @click="goToHome">replace go home</a>
    </p>
    <p>
      <button @click="upHrefToHome">up href to home</button>
    </p>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue';

const url = ref("");

function goToHome() {
  // this.$router.replace('/')
  // 作为子应用这里是一个 `bug`，会将链接替换成基座 http://localhost:3000/ 然后报错
  window.location.replace('http://localhost:8080/');
}

function upHrefToHome() {
  // 在降级处理中这里是一个 `bug`，因为 `location` 并没有劫持，造成 `/` 指向基座首页，和上面 `replace` 一样的错误
  console.log(window.location.href);
  window.location.href = "/";
}

onMounted(() => {
  url.value = window.location.href;
});
</script>