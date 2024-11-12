<template>
  <nav class="fixed bottom-0 left-0 right-0 bg-white border-t">
    <div class="flex justify-around py-2">
      <div v-for="item in navigation" :key="item.name"
           class="flex flex-col items-center">
        <i class="mb-1 text-lg" :class="{ 'text-primary-600': item.active }">
          {{ item.icon }}
        </i>
        <span class="text-xs" :class="{ 'text-primary-600': item.active }">
          {{ item.name }}
        </span>
      </div>
    </div>
  </nav>
</template>

<script setup>
const navigation = ref([
  { name: '首页', icon: '🏠', active: true },
  { name: '行程', icon: '🗺️', active: false },
  { name: '订单', icon: '📋', active: false },
  { name: '购物车', icon: '🛒', active: false },
  { name: '我的', icon: '👤', active: false }
])
</script>