<script setup lang="ts">
defineProps<{
  title: string;
  description: string;
  image: string;
  price: number;
}>();
const formatPrice = (price: number) => price.toFixed(2);
</script>
<template>
  <div
    class="shadow-lg flex flex-col rounded-lg gap-4 p-5 text-sm border border-gray-200 min-w-[276px] h-[422px]"
  >
    <span class="font-normal text-[20px]">{{ title }}</span>
    <picture class="flex justify-center w-full">
      <img :src="image" alt="{description}" class="w-[200px]" />
    </picture>
    <div class="w-[138px] h-[2px] bg-[#01513F]" />
    <div class="flex flex-col gap-5">
      <span class="text-[#BDBDBD] text-[12px] font-normal">{{
        description
      }}</span>
      <span class="font-normal text-[16px]">S/. {{ formatPrice(price) }}</span>
    </div>
  </div>
</template>
