<script setup>
import { ref, computed } from 'vue'

// State (Data reaktif)
const newItem = ref('')
const newQuantity = ref(1)
const searchQuery = ref('')
const filterStatus = ref('all') // 'all', 'active', 'completed'

const items = ref([
  { id: 1, name: 'Susu UHT', quantity: 2, completed: false },
  { id: 2, name: 'Roti Tawar', quantity: 1, completed: true },
  { id: 3, name: 'Telur Ayam', quantity: 12, completed: false }
])

// Tambah item baru
const addItem = () => {
  if (!newItem.value.trim()) return
  items.value.push({
    id: Date.now(),
    name: newItem.value,
    quantity: newQuantity.value,
    completed: false
  })
  newItem.value = ''
  newQuantity.value = 1
}

// Hapus item
const removeItem = (id) => {
  items.value = items.value.filter(item => item.id !== id)
}

// Computed: Filter berdasarkan pencarian dan status
const filteredItems = computed(() => {
  return items.value.filter(item => {
    const matchesSearch = item.name.toLowerCase().includes(searchQuery.value.toLowerCase())
    if (filterStatus.value === 'active') return matchesSearch && !item.completed
    if (filterStatus.value === 'completed') return matchesSearch && item.completed
    return matchesSearch
  })
})
</script>

<template>
  <div class="min-h-screen bg-slate-100 flex items-center justify-center p-4">
    <div class="bg-white w-full max-w-md rounded-xl shadow-lg p-6">
      
      <!-- Judul -->
      <h1 class="text-2xl font-bold text-slate-800 mb-4 text-center">🛒 VueShop List</h1>

      <!-- Form Input -->
      <form @submit.prevent="addItem" class="flex gap-2 mb-4">
        <input 
          v-model="newItem" 
          type="text" 
          placeholder="Nama barang..." 
          class="flex-1 border border-slate-300 rounded-lg px-3 py-2 text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500"
        />
        <input 
          v-model.number="newQuantity" 
          type="number" 
          min="1" 
          class="w-16 border border-slate-300 rounded-lg px-2 py-2 text-sm text-center focus:outline-none focus:ring-2 focus:ring-indigo-500"
        />
        <button 
          type="submit" 
          class="bg-indigo-600 text-white px-4 py-2 rounded-lg text-sm font-medium hover:bg-indigo-700 transition"
        >
          Tambah
        </button>
      </form>

      <!-- Pencarian & Filter -->
      <div class="flex flex-col sm:flex-row gap-2 mb-4">
        <input 
          v-model="searchQuery" 
          type="text" 
          placeholder="Cari barang..." 
          class="flex-1 border border-slate-300 rounded-lg px-3 py-1.5 text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500"
        />
        <select 
          v-model="filterStatus" 
          class="border border-slate-300 rounded-lg px-3 py-1.5 text-sm bg-white focus:outline-none focus:ring-2 focus:ring-indigo-500"
        >
          <option value="all">Semua</option>
          <option value="active">Belum</option>
          <option value="completed">Selesai</option>
        </select>
      </div>

      <!-- Daftar Item -->
      <ul class="space-y-2 mb-4 max-h-60 overflow-y-auto">
        <li v-if="filteredItems.length === 0" class="text-center text-slate-400 py-4 text-sm">
          Tidak ada barang ditemukan.
        </li>
        <li 
          v-for="item in filteredItems" 
          :key="item.id"
          class="flex items-center justify-between p-3 rounded-lg border border-slate-200 transition hover:bg-slate-50"
          :class="{ 'bg-slate-50 opacity-75': item.completed }"
        >
          <div class="flex items-center gap-3 cursor-pointer flex-1" @click="item.completed = !item.completed">
            <input type="checkbox" v-model="item.completed" class="w-4 h-4 text-indigo-600 rounded" />
            <span :class="{ 'line-through text-slate-400': item.completed }" class="text-slate-700 text-sm font-medium">
              {{ item.name }} <span class="text-xs text-slate-500">(x{{ item.quantity }})</span>
            </span>
          </div>
          <button 
            @click="removeItem(item.id)" 
            class="text-red-500 hover:text-red-700 text-sm px-2 py-1"
          >
            ✕
          </button>
        </li>
      </ul>

      <!-- Footer Info -->
      <div class="text-xs text-slate-500 text-center border-t pt-3">
        Total item ditampilkan: {{ filteredItems.length }}
      </div>

    </div>
  </div>
</template>