<script setup>
import { useRouter } from 'vue-router'
const router = useRouter()

const goHome = () => router.push('/')
const goChat = () => router.push('/chat')
</script>

<template>
  <div class="min-h-screen bg-radial-[at_50%_5%] from-white via-white to-blue-100 flex items-center justify-center px-6">

    <div class="text-center max-w-2xl">

      <!-- 404 number -->
      <h1 class="text-8xl font-extrabold text-indigo-600 mb-4">
        404
      </h1>

      <!-- Title -->
      <h2 class="text-3xl md:text-4xl font-bold text-slate-900 mb-4">
        Oops… Page not found 😢
      </h2>

      <!-- Subtitle -->
      <p class="text-slate-600 text-lg leading-relaxed mb-10">
        The page you are looking for doesn’t exist or may have been moved.
        Let’s take you back to learning Computer Science in Yorùbá.
      </p>

      <!-- Actions -->
      <div class="flex flex-wrap justify-center gap-4">
        <button
          @click="goHome"
          class="px-6 py-3 rounded-full text-white bg-indigo-600 hover:bg-indigo-700 font-medium transition">
          Go Home
        </button>

        <button
          @click="goChat"
          class="px-6 py-3 rounded-full border border-indigo-600 text-slate-900 hover:bg-indigo-100 font-medium transition">
          Go to Chat
        </button>
      </div>

      <!-- small hint -->
      <p class="mt-10 text-slate-500">
        Error code: 404 • Page Not Found
      </p>

    </div>

  </div>
</template>
