<template>
  <div class="space-y-8">
    <section class="text-center py-12">
      <h1 class="text-4xl font-bold mb-4">금속공예 공방에 오신 것을 환영합니다</h1>
      <p class="text-xl text-gray-600">전통과 현대가 조화를 이루는 특별한 금속공예 작품을 만나보세요</p>
    </section>

    <section class="grid grid-cols-1 md:grid-cols-3 gap-6">
      <div v-for="(feature, index) in features" :key="index" class="p-6 bg-white rounded-lg shadow-md">
        <h3 class="text-xl font-semibold mb-2">{{ feature.title }}</h3>
        <p class="text-gray-600">{{ feature.description }}</p>
      </div>
    </section>

    <section class="text-center py-8">
      <NuxtLink to="/works" class="bg-gray-800 text-white px-6 py-3 rounded-lg hover:bg-gray-700">
        작품 보기
      </NuxtLink>
    </section>
  </div>
</template>

<script setup lang="ts">
interface Feature {
  title: string;
  description: string;
}

const features: Feature[] = [
  {
    title: '전통 공예',
    description: '전통적인 금속공예 기법을 현대적으로 재해석합니다.'
  },
  {
    title: '맞춤 제작',
    description: '고객의 요구사항에 맞춘 특별한 작품을 제작합니다.'
  },
  {
    title: '체험 프로그램',
    description: '금속공예의 매력을 직접 체험할 수 있는 프로그램을 운영합니다.'
  }
];
</script> 