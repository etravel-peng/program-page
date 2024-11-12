<template>
  <div class="min-h-screen bg-gray-50">
    <!-- Header -->
    <div class="bg-primary-600 text-white p-4 flex items-center">
      <button class="mr-4" @click="router.back()">
        <span class="text-xl">←</span>
      </button>
      <h1 class="text-lg font-medium">直通车服务</h1>
    </div>

    <!-- Search Form -->
    <div class="bg-white p-4 shadow-md">
      <div class="space-y-4">
        <!-- Station Selection -->
        <div class="flex items-center">
          <div class="flex-1">
            <select v-model="departure" class="w-full p-2 border rounded-lg">
              <option value="">选择出发站</option>
              <option v-for="station in stations" :key="station">{{ station }}</option>
            </select>
          </div>
          <div class="px-4 text-gray-400">→</div>
          <div class="flex-1">
            <select v-model="destination" class="w-full p-2 border rounded-lg">
              <option value="">选择目的地</option>
              <option v-for="station in stations" :key="station">{{ station }}</option>
            </select>
          </div>
        </div>

        <!-- Date Selection -->
        <div class="relative">
          <input type="date" v-model="travelDate" 
                 class="w-full p-2 border rounded-lg"
                 :min="today">
        </div>

        <!-- Search Button -->
        <button @click="search" 
                class="w-full bg-primary-600 text-white py-3 rounded-lg font-medium">
          查询车票
        </button>
      </div>
    </div>

    <!-- Results Tabs -->
    <div class="bg-white mt-2" v-if="showResults">
      <div class="flex border-b">
        <button v-for="tab in tabs" 
                :key="tab.id"
                @click="activeTab = tab.id"
                class="flex-1 py-3 text-center"
                :class="{'text-primary-600 border-b-2 border-primary-600': activeTab === tab.id}">
          {{ tab.name }}
        </button>
      </div>

      <!-- Bus Tickets Results -->
      <div v-if="activeTab === 'bus'" class="p-4 space-y-4">
        <div v-for="ticket in busTickets" 
             :key="ticket.id"
             class="bg-white border rounded-lg p-4">
          <div class="flex justify-between items-start mb-3">
            <div>
              <div class="text-lg font-medium">{{ ticket.departureTime }}</div>
              <div class="text-sm text-gray-500">{{ ticket.distance }}公里</div>
            </div>
            <div class="text-right">
              <div class="text-primary-600 font-bold">¥{{ ticket.currentPrice }}</div>
              <div class="text-xs text-gray-500 line-through">原价: ¥{{ ticket.originalPrice }}</div>
              <div class="text-xs text-red-500">优惠: ¥{{ ticket.discount }}</div>
            </div>
          </div>
          
          <div class="flex justify-between text-sm">
            <div>
              <div>{{ ticket.from }} → {{ ticket.to }}</div>
              <div class="text-gray-500">{{ ticket.type }}</div>
            </div>
            <div class="text-right">
              <div class="text-gray-500">剩余: {{ ticket.stock }}张</div>
              <button class="mt-2 px-4 py-1 bg-primary-600 text-white rounded-lg">
                预订
              </button>
            </div>
          </div>
        </div>
      </div>

      <!-- Intercity Scenic Results -->
      <div v-if="activeTab === 'scenic'" class="p-4 space-y-4">
        <div v-for="route in scenicRoutes" 
             :key="route.id"
             class="bg-white border rounded-lg p-4">
          <div class="flex justify-between items-start mb-3">
            <div>
              <div class="text-lg font-medium">{{ route.departureTime }}</div>
              <div class="text-sm text-gray-500">全程{{ route.duration }}</div>
            </div>
            <div class="text-right">
              <div class="text-primary-600 font-bold">¥{{ route.currentPrice }}</div>
              <div class="text-xs text-gray-500 line-through">原价: ¥{{ route.originalPrice }}</div>
              <div class="text-xs text-red-500">优惠: ¥{{ route.discount }}</div>
            </div>
          </div>
          
          <div class="flex justify-between text-sm">
            <div>
              <div>{{ route.from }} → {{ route.to }}</div>
              <div class="text-gray-500">
                {{ route.stops }}站 | {{ route.vehicleType }}
              </div>
            </div>
            <div class="text-right">
              <div class="text-gray-500">剩余: {{ route.stock }}张</div>
              <button class="mt-2 px-4 py-1 bg-primary-600 text-white rounded-lg">
                预订
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const router = useRouter()
const departure = ref('')
const destination = ref('')
const travelDate = ref('')
const activeTab = ref('bus')
const showResults = ref(false)

const today = new Date().toISOString().split('T')[0]

const tabs = [
  { id: 'bus', name: '汽车票' },
  { id: 'scenic', name: '城际景区' }
]

const stations = [
  '市中心站',
  '东部汽车站',
  '西站',
  '南站',
  '北站',
  '机场',
  '西湖景区',
  '千岛湖景区'
]

const busTickets = ref([
  {
    id: 1,
    departureTime: '08:30',
    distance: '45',
    from: '市中心站',
    to: '西湖景区',
    type: '直达车',
    originalPrice: 35,
    currentPrice: 28,
    discount: 7,
    stock: 12
  },
  {
    id: 2,
    departureTime: '09:00',
    distance: '50',
    from: '市中心站',
    to: '西湖景区',
    type: '过路车',
    originalPrice: 30,
    currentPrice: 25,
    discount: 5,
    stock: 8
  }
])

const scenicRoutes = ref([
  {
    id: 1,
    departureTime: '08:00',
    duration: '90分钟',
    from: '市中心站',
    to: '千岛湖景区',
    stops: '3',
    vehicleType: '豪华大巴',
    originalPrice: 88,
    currentPrice: 68,
    discount: 20,
    stock: 15
  },
  {
    id: 2,
    departureTime: '09:30',
    duration: '60分钟',
    from: '市中心站',
    to: '西湖景区',
    stops: '2',
    vehicleType: '商务车',
    originalPrice: 128,
    currentPrice: 98,
    discount: 30,
    stock: 6
  }
])

const search = () => {
  if (departure.value && destination.value && travelDate.value) {
    showResults.value = true
  }
}
</script>