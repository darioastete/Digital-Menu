<script setup lang="ts">
import { onMounted, ref } from "vue";
import { menuItems } from "../consts/MenuItem";
import Card from "./Card.vue";
const queue = ref(menuItems);
const handleUrlChange = () => {
  const query = new URLSearchParams(window.location.search).get("q");
  queue.value = query
    ? menuItems.filter((item) => item.slug === query)
    : menuItems;
};

onMounted(() => {
  window.addEventListener("popstate", handleUrlChange);
  window.addEventListener("pushstate", handleUrlChange);
  window.addEventListener("replacestate", handleUrlChange);
});
</script>
<template>
  <template v-for="item in queue">
    <Card
      :title="item.title"
      :description="item.description"
      :image="item.image"
      :price="item.price"
    />
  </template>
</template>
