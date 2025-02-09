<template>
  <div class="fixed top-0 left-0 size-full bg-black z-10 opacity-50">fff</div>
  <div class="bg-white w-96 h-full fixed top-0 right-0 z-20 p-7">
    <div class="flex items-center gap-3 mb-5">
      <span class="text-3xl cursor-pointer">&#8592;</span>
      <h2 class="text-2xl font-bold">Корзина</h2>
    </div>
    <CartList />
    <div class="flex flex-col gap-4">
      <div class="flex justify-between">Итого <span class="font-bold">11</span></div>
      <div class="flex justify-between">Налог <span class="font-bold">11</span></div>
      <button
        type="button"
        class="px-8 py-5 border border-green-500 bg-green-200 rounded-3xl disabled:bg-slate-400"
      >
        Оплатить
      </button>
    </div>
  </div>
</template>
<script setup>
import CartList from './CartList.vue'
</script>
<style></style>
