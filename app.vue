<template>
  <div>
    <header class="bg-gray-800 text-white p-4">
      <nav class="container mx-auto flex justify-between items-center">
        <NuxtLink to="/" class="text-xl font-bold">금속공예 공방</NuxtLink>
        <div class="space-x-4">
          <NuxtLink to="/" class="hover:text-gray-300">홈</NuxtLink>
          <NuxtLink to="/about" class="hover:text-gray-300">소개</NuxtLink>
          <NuxtLink to="/works" class="hover:text-gray-300">작품</NuxtLink>
          <NuxtLink to="/contact" class="hover:text-gray-300">문의</NuxtLink>
        </div>
      </nav>
    </header>

    <main class="container mx-auto p-4">
      <NuxtPage />
    </main>

    <footer class="bg-gray-800 text-white p-4 mt-8">
      <div class="container mx-auto text-center">
        <p>&copy; 2024 금속공예 공방. All rights reserved.</p>
      </div>
    </footer>
  </div>
</template>

<script setup lang="ts">
// TypeScript 설정
</script>
