<template>
  <div class="bg-white rounded-lg shadow-md p-4">
    <div class="flex justify-between items-center mb-4">
      <div>
        <div class="text-lg font-medium">{{ route.terminal }}</div>
        <div class="text-sm text-gray-500">至 {{ route.destination }}</div>
      </div>
      <div class="text-primary-600 font-bold">¥{{ route.price }}</div>
    </div>
    
    <div class="flex justify-between items-end">
      <div class="text-sm text-gray-500">
        <div>行程时间: {{ route.duration }}</div>
        <div>发车频率: {{ route.frequency }}</div>
        <div class="flex space-x-2 mt-2">
          <span v-if="route.hasWifi" class="text-xs bg-primary-50 text-primary-600 px-2 py-1 rounded">
            WiFi
          </span>
          <span v-if="route.hasCharging" class="text-xs bg-primary-50 text-primary-600 px-2 py-1 rounded">
            充电插座
          </span>
        </div>
      </div>
      <button class="bg-primary-600 text-white px-4 py-2 rounded-lg text-sm">
        预订
      </button>
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