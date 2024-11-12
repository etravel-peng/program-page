<template>
  <div class="bg-white rounded-lg shadow-md overflow-hidden">
    <img :src="route.image" class="w-full h-48 object-cover" />
    <div class="p-4">
      <div class="flex justify-between items-start mb-3">
        <h3 class="text-lg font-medium">{{ route.name }}</h3>
        <div class="text-primary-600 font-bold">¥{{ route.price }}</div>
      </div>
      
      <div class="text-sm text-gray-500 mb-3">
        <div>行程时间: {{ route.duration }}</div>
        <div class="flex items-center mt-1">
          <span class="text-yellow-400">★</span>
          <span class="ml-1">{{ route.rating }}</span>
        </div>
      </div>

      <div class="flex flex-wrap gap-2">
        <span v-for="feature in route.includes" 
              :key="feature"
              class="text-xs bg-primary-50 text-primary-600 px-2 py-1 rounded">
          {{ feature }}
        </span>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  route: {
    type: Object,
    required: true
  }
})
</script>