<template>
  <div class="relative overflow-hidden">
    <div class="flex transition-transform duration-500 ease-in-out" :style="{ transform: `translateX(-${currentIndex * 100}%)` }">
      <div v-for="(image, index) in images" :key="index" class="w-full flex-shrink-0">
        <img :src="image.url" :alt="image.alt" class="w-full h-[400px] object-cover">
      </div>
    </div>
    
    <!-- 네비게이션 버튼 -->
    <button @click="prev" class="absolute left-4 top-1/2 transform -translate-y-1/2 bg-black bg-opacity-50 text-white p-2 rounded-full hover:bg-opacity-75">
      <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
      </svg>
    </button>
    <button @click="next" class="absolute right-4 top-1/2 transform -translate-y-1/2 bg-black bg-opacity-50 text-white p-2 rounded-full hover:bg-opacity-75">
      <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
      </svg>
    </button>

    <!-- 인디케이터 -->
    <div class="absolute bottom-4 left-0 right-0 flex justify-center space-x-2">
      <button v-for="(_, index) in images" :key="index"
        @click="currentIndex = index"
        class="w-3 h-3 rounded-full transition-colors duration-300"
        :class="currentIndex === index ? 'bg-white' : 'bg-white/50'">
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
interface Image {
  url: string;
  alt: string;
}

const images: Image[] = [
  {
    url: '/images/ring.jpg',
    alt: '은반지 작품'
  },
  {
    url: '/images/necklace.jpg',
    alt: '목걸이 작품'
  },
  {
    url: '/images/bracelet.jpg',
    alt: '팔찌 작품'
  }
];

const currentIndex = ref(0);

const next = () => {
  currentIndex.value = (currentIndex.value + 1) % images.length;
};

const prev = () => {
  currentIndex.value = (currentIndex.value - 1 + images.length) % images.length;
};

// 자동 슬라이드
onMounted(() => {
  setInterval(next, 5000);
});
</script> 