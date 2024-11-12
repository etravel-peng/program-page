<template>
  <div class="bg-white rounded-lg shadow-lg p-6 mb-6">
    <!-- Primary Actions -->
    <div class="grid grid-cols-2 gap-4 mb-6">
      <div v-for="action in primaryActions" :key="action.id" 
           class="flex flex-col items-center cursor-pointer"
           @click="$emit('select-category', action.id)">
        <div class="w-16 h-16 bg-primary-50 rounded-full flex items-center justify-center mb-2">
          <i class="text-2xl text-primary-600">{{ action.icon }}</i>
        </div>
        <span class="text-sm font-medium">{{ action.name }}</span>
        <span class="text-xs text-gray-500">{{ action.desc }}</span>
      </div>
    </div>

    <!-- Secondary Actions -->
    <div class="grid grid-cols-4 gap-4">
      <div v-for="action in secondaryActions" :key="action.id"
           class="flex flex-col items-center cursor-pointer"
           @click="$emit('select-category', action.id)">
        <div class="w-12 h-12 bg-gray-50 rounded-full flex items-center justify-center mb-1">
          <i class="text-xl text-gray-600">{{ action.icon }}</i>
        </div>
        <span class="text-xs">{{ action.name }}</span>
      </div>
    </div>
  </div>
</template>

<script setup>
const primaryActions = [
  { id: 'direct-bus', name: '直通车', desc: '景区直达', icon: '🚌' },
  { id: 'tour-ticket', name: '车+玩乐体验', desc: '特惠预订', icon: '🎫' }
]

const secondaryActions = [
  { id: 'car-rental', name: '包车租车', icon: '🚗' },
  { id: 'fun-ticket', name: '玩乐门票', icon: '🎤' },
  { id: 'souvenirs', name: '文创商品', icon: '🎁' },
  { id: 'stations', name: '停靠站点', icon: '📍' }
]

defineEmits(['select-category'])
</script>