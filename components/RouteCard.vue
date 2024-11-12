<template>
  <div class="bg-white rounded-lg shadow-md p-4">
    <div class="flex justify-between items-center mb-4">
      <div class="flex items-center space-x-4">
        <div class="text-lg font-medium">{{ route.from }}</div>
        <span class="text-gray-400">→</span>
        <div class="text-lg font-medium">{{ route.to }}</div>
      </div>
      <div class="text-primary-600 font-bold">¥{{ route.price }}</div>
    </div>
    
    <div class="flex justify-between text-sm text-gray-500">
      <div>
        <div>行程时间: {{ route.duration }}</div>
        <div>发车间隔: {{ route.schedule }}</div>
      </div>
      <div class="text-right">
        <div class="text-primary-600">下次发车</div>
        <div class="font-medium">{{ route.nextDeparture }}</div>
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