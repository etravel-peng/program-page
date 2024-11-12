<template>
  <div class="relative h-64 bg-cover bg-center" :style="{ backgroundImage: `url(${bannerImage})` }">
    <div class="absolute inset-0 bg-gradient-to-b from-transparent to-black/30">
      <div class="container mx-auto px-4 pt-12">
        <div class="w-12 h-12 mb-2 bg-white/10 rounded-full flex items-center justify-center">
          <span class="text-2xl">🏞️</span>
        </div>
        <h1 class="text-2xl font-bold text-white mb-1">{{ title }}</h1>
        <p class="text-sm text-white/90">{{ subtitle }}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  bannerImage: {
    type: String,
    default: 'https://picsum.photos/800/400'
  },
  title: {
    type: String,
    default: '景区直通'
  },
  subtitle: {
    type: String,
    default: '便捷出行 | 景点直达'
  }
})
</script>