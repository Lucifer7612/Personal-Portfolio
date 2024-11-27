<template>
  <div>Admin Side</div>
  <button @click="takeData">Data</button>

  <div class="flex flex-wrap items-center justify-center gap-5">
    <div class="w-auto p-7 bg-blue-200" v-for="i in list" :key="i.id">
      <h2>User Name: {{ i.name }}</h2>
      <h2>Email: {{ i.email }}</h2>
      <h2>What Help they need:{{ i.help }}</h2>
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";
import { axiosApi } from "./lib/axios";
const list = ref([]);

const takeData = async () => {
  try {
    const response = await axiosApi.get("/api/users");
    list.value = response.data;
    console.log(list.value);
  } catch (error) {
    console.error("Error fetching data:", error);
  }
};
</script>
