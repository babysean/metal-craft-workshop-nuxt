<template>
  <div class="max-w-4xl mx-auto space-y-8">
    <section class="text-center py-8">
      <h1 class="text-4xl font-bold mb-4">문의하기</h1>
      <p class="text-xl text-gray-600">작품 주문이나 문의사항이 있으시다면 언제든 연락주세요</p>
    </section>

    <section class="grid grid-cols-1 md:grid-cols-2 gap-8">
      <!-- 연락처 정보 -->
      <div class="space-y-6">
        <h2 class="text-2xl font-semibold">연락처 정보</h2>
        <div class="space-y-4">
          <div class="flex items-center space-x-3">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" />
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" />
            </svg>
            <span>서울특별시 종로구 금속공예로 123</span>
          </div>
          <div class="flex items-center space-x-3">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" />
            </svg>
            <span>02-1234-5678</span>
          </div>
          <div class="flex items-center space-x-3">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
            </svg>
            <span>info@metalcraft.com</span>
          </div>
        </div>

        <div class="mt-8">
          <h3 class="text-lg font-semibold mb-4">영업시간</h3>
          <div class="space-y-2">
            <p>평일: 10:00 - 19:00</p>
            <p>토요일: 10:00 - 17:00</p>
            <p>일요일: 휴무</p>
          </div>
        </div>
      </div>

      <!-- 문의 폼 -->
      <div class="bg-white p-6 rounded-lg shadow-md">
        <form @submit.prevent="handleSubmit" class="space-y-4">
          <div>
            <label for="name" class="block text-sm font-medium text-gray-700">이름</label>
            <input
              type="text"
              id="name"
              v-model="form.name"
              class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-gray-500 focus:ring-gray-500"
              required
            >
          </div>
          <div>
            <label for="email" class="block text-sm font-medium text-gray-700">이메일</label>
            <input
              type="email"
              id="email"
              v-model="form.email"
              class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-gray-500 focus:ring-gray-500"
              required
            >
          </div>
          <div>
            <label for="phone" class="block text-sm font-medium text-gray-700">전화번호</label>
            <input
              type="tel"
              id="phone"
              v-model="form.phone"
              class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-gray-500 focus:ring-gray-500"
              required
            >
          </div>
          <div>
            <label for="message" class="block text-sm font-medium text-gray-700">문의내용</label>
            <textarea
              id="message"
              v-model="form.message"
              rows="4"
              class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-gray-500 focus:ring-gray-500"
              required
            ></textarea>
          </div>
          <button
            type="submit"
            class="w-full bg-gray-800 text-white py-2 px-4 rounded-md hover:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-gray-500 focus:ring-offset-2"
          >
            문의하기
          </button>
        </form>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
interface FormData {
  name: string;
  email: string;
  phone: string;
  message: string;
}

const form = ref<FormData>({
  name: '',
  email: '',
  phone: '',
  message: ''
});

const handleSubmit = () => {
  // 여기에 폼 제출 로직 구현
  console.log('Form submitted:', form.value);
  // 폼 초기화
  form.value = {
    name: '',
    email: '',
    phone: '',
    message: ''
  };
};
</script> 