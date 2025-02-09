<script setup>
import { onMounted, reactive, ref, watch } from 'vue'
import axios from 'axios'
import Header from './components/HeaderComponent.vue'
import CardList from './components/CardList.vue'

// import Drawer from './components/DrawerComponent.vue'
const items = ref([])

const filters = reactive({ sortBy: 'title', searchQuery: '' })
const fetchItems = async () => {
  const params = {
    sortBy: filters.sortBy,
  }
  if (filters.searchQuery) {
    params.title = `*${filters.searchQuery}*`
  }
  try {
    const { data } = await axios.get(`https://830041bab49eca92.mokky.dev/items`, { params })
    items.value = data
  } catch (e) {
    console.log(e)
  }
}

onMounted(fetchItems)

const onChangeSelect = (event) => {
  filters.sortBy = event.target.value
}
const onChangeSeatchInput = (event) => {
  filters.searchQuery = event.target.value
}

watch(filters, fetchItems, { deep: true })
</script>

<template>
  <!-- <Drawer /> -->
  <div class="w-4/5 bg-slate-100 m-auto rounded-2xl shadow-xl mt-10">
    <Header />
    <div class="flex justify-between px-10 py-4 items-center">
      <h2 class="text-3xl font-bold">Все кроссовки</h2>
      <div class="flex gap-5">
        <select @change="onChangeSelect" class="outline-none rounded-xl">
          <option value="name">По названию</option>
          <option value="price">По цене(дешевые)</option>
          <option value="-price">По цене(дорогие)</option>
        </select>
        <input
          @input="onChangeSeatchInput"
          type="text"
          placeholder="Поиск"
          class="border border-gray-300 bg-transparent px-3 py-2 outline-none focus:border-gray-500 rounded-xl"
        />
      </div>
    </div>
    <CardList :items="items" />
  </div>
</template>

<style scoped></style>
