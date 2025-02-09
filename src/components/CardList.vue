<template>
  <div class="p-10">
    <div class="grid grid-cols-4 gap-7">
      <Card
        v-for="item in items"
        :img="item.imageUrl"
        :price="item.price"
        :title="item.title"
        :key="item.id"
      />
    </div>
  </div>
</template>
<script setup>
import Card from './CardComponent.vue'

defineProps({
  items: Array,
})
</script>
<style></style>
