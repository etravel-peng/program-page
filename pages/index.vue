<template>
  <div class="min-h-screen bg-gray-50 pb-16">
    <HeaderBanner />
    
    <div class="container mx-auto px-4 -mt-8">
      <QuickActions @select-category="navigateToCategory" />
      <UserCard />
      
      <!-- Featured Tours -->
      <div class="mb-6">
        <div class="flex justify-between items-center mb-4">
          <h2 class="text-lg font-bold">热门线路</h2>
          <span class="text-sm text-primary-600">查看更多</span>
        </div>
        <div class="grid grid-cols-2 gap-4">
          <div v-for="tour in tours" :key="tour.id" 
               class="bg-white rounded-lg shadow overflow-hidden">
            <img :src="tour.image" class="w-full h-32 object-cover" />
            <div class="p-3">
              <h3 class="font-medium text-sm mb-1">{{ tour.name }}</h3>
              <p class="text-primary-600 text-sm">¥{{ tour.price }}起</p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <BottomNav />
  </div>
</template>

<script setup>
const router = useRouter()

const tours = ref([
  { 
    id: 1, 
    name: '城市观光一日游', 
    price: 199, 
    image: 'https://picsum.photos/400/300?random=1'
  },
  { 
    id: 2, 
    name: '古镇深度游', 
    price: 299, 
    image: 'https://picsum.photos/400/300?random=2'
  }
])

const navigateToCategory = (categoryId) => {
  if (categoryId === 'direct-bus') {
    router.push('/direct-bus')
  }
}
</script>