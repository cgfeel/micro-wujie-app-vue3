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
  // 作为子应用这里是一个 `bug`
  window.location.replace('http://localhost:8080/');
}

function upHrefToHome() {
  window.location.href = "/";
}

onMounted(() => {
  url.value = window.location.href;
});
</script>