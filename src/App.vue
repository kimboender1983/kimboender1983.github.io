<template>

  <v-layout class="rounded rounded-md">
    <v-app-bar title="Todos"></v-app-bar>

    <v-navigation-drawer>
      <!-- <v-list>
        <v-list-item title="Navigation drawer"></v-list-item>
      </v-list> -->
    </v-navigation-drawer>

    <v-main class="d-flex align-center justify-center" style="min-height: 300px;">
      <v-row>
        <v-col>
          <v-data-table
            :headers="headers"
            :items="todos"
            item-value="name"
            :items-per-page="50"
            :item-selectable="true"
          ></v-data-table>

        </v-col>
      </v-row>
    </v-main>
  </v-layout>
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";

const headers = [
  { title: 'Title', key: 'title' },
  { title: 'Completed', key: 'completed' }
]

const todos = ref([]);

async function getTodos() {
  const req = await fetch('https://jsonplaceholder.typicode.com/todos');

  const res = await req.json();

  todos.value = res;
}

onMounted(() => getTodos());
</script>
