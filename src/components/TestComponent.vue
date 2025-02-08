<!-- <script>
export default {
  data() {
    return {
      count: 0,
    }
  },
  methods: {
    increment() {
      this.count++
    },
    decrement() {
      this.count--
    },
  },
}
</script> -->
<script setup>
defineProps({
  title: String,
})
</script>
<template>
  <div class="border p-4">
    {{ title }}
  </div>
</template>
<style scoped></style>
