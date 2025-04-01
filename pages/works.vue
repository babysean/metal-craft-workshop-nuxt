<template>
  <div class="max-w-6xl mx-auto space-y-8">
    <section class="text-center py-8">
      <h1 class="text-4xl font-bold mb-4">작품 갤러리</h1>
      <p class="text-xl text-gray-600">우리 공방의 대표 작품들을 만나보세요</p>
    </section>

    <!-- 카테고리 필터 -->
    <section class="flex justify-center space-x-4">
      <button 
        v-for="category in categories" 
        :key="category.id"
        @click="selectedCategory = category.id"
        class="px-4 py-2 rounded-full transition-colors"
        :class="selectedCategory === category.id ? 'bg-gray-800 text-white' : 'bg-gray-100 text-gray-800 hover:bg-gray-200'"
      >
        {{ category.name }}
      </button>
    </section>

    <!-- 작품 그리드 -->
    <section class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
      <div v-for="work in filteredWorks" :key="work.id" class="bg-white rounded-lg shadow-md overflow-hidden">
        <div class="relative h-[300px]">
          <img :src="work.image" :alt="work.title" class="w-full h-full object-cover">
        </div>
        <div class="p-4">
          <h3 class="text-xl font-semibold mb-2">{{ work.title }}</h3>
          <p class="text-gray-600 mb-4">{{ work.description }}</p>
          <div class="flex justify-between items-center">
            <span class="text-gray-800 font-medium">{{ work.price }}</span>
            <button class="bg-gray-800 text-white px-4 py-2 rounded hover:bg-gray-700">
              문의하기
            </button>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
interface Category {
  id: string;
  name: string;
}

interface Work {
  id: number;
  title: string;
  description: string;
  image: string;
  price: string;
  category: string;
}

const categories: Category[] = [
  { id: 'all', name: '전체' },
  { id: 'ring', name: '반지' },
  { id: 'necklace', name: '목걸이' },
  { id: 'bracelet', name: '팔찌' },
  { id: 'earring', name: '귀걸이' }
];

const works: Work[] = [
  {
    id: 1,
    title: '은반지 - 달빛',
    description: '달빛을 닮은 은반지로, 은의 부드러운 광택이 특징입니다.',
    image: '/images/ring.jpg',
    price: '150,000원',
    category: 'ring'
  },
  {
    id: 2,
    title: '목걸이 - 별빛',
    description: '별이 반짝이는 듯한 디자인의 목걸이입니다.',
    image: '/images/necklace.jpg',
    price: '280,000원',
    category: 'necklace'
  },
  {
    id: 3,
    title: '팔찌 - 꽃길',
    description: '꽃이 피어있는 듯한 아름다운 디자인의 팔찌입니다.',
    image: '/images/bracelet.jpg',
    price: '200,000원',
    category: 'bracelet'
  },
  {
    id: 4,
    title: '귀걸이 - 새싹',
    description: '봄의 새싹을 형상화한 귀걸이입니다.',
    image: '/images/earring.jpg',
    price: '180,000원',
    category: 'earring'
  }
];

const selectedCategory = ref('all');

const filteredWorks = computed(() => {
  if (selectedCategory.value === 'all') return works;
  return works.filter(work => work.category === selectedCategory.value);
});
</script> 