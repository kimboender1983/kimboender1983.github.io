<template>
  {{ todos }}
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";

const todos = ref([]);

async function getTodos() {
  const req = await fetch('https://jsonplaceholder.typicode.com/todos');

  const res = await req.json();

  todos.value = res;
}

onMounted(() => getTodos());
</script>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
