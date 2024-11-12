<template>
  <div class="bg-white rounded-lg shadow p-4 mb-6">
    <div class="flex items-center justify-between">
      <div class="flex items-center">
        <div class="w-12 h-12 rounded-full bg-gray-100 flex items-center justify-center">
          <span class="text-2xl">👤</span>
        </div>
        <div class="ml-3">
          <p class="font-medium">{{ greeting }}</p>
          <p class="text-xs text-gray-500">{{ welcomeMessage }}</p>
        </div>
      </div>
      <div class="flex items-center space-x-6">
        <div class="text-center">
          <p class="text-sm font-medium">优惠券</p>
          <p class="text-xs text-gray-500">{{ coupons }}张</p>
        </div>
        <div class="text-center">
          <p class="text-sm font-medium">积分</p>
          <p class="text-xs text-gray-500">{{ points }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  greeting: {
    type: String,
    default: '游客您好'
  },
  welcomeMessage: {
    type: String,
    default: '欢迎来到景区直通'
  },
  coupons: {
    type: Number,
    default: 2
  },
  points: {
    type: Number,
    default: 88
  }
})
</script>