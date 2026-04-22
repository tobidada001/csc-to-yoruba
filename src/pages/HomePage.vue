<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';


  const inputRef = ref('')
  const errorRef = ref('')

  const router = useRouter()

  const redirectUser = () => {

    if(inputRef.value.trim() == ''){
      errorRef.value = "The search field cannot be empty"
      return
    }

    errorRef.value = ''

    router.push({name: 'chat', query: {search: inputRef.value}} )

  }
</script>

<template>

  <div class="bg-radial-[at_50%_5%] from-white via-white to-blue-100">
  <header class="bg-transparent flex py-2 px-4 sm:px-10 min-h-21 tracking-wide z-50">
    <div class="flex flex-wrap items-center justify-between gap-5 w-full max-w-screen-xl mx-auto">
      <a href="#" class="max-sm:hidden text-2xl font-bold text-indigo-700">YorubaAI</a>
      <a href="#" class="hidden max-sm:block text-xl font-bold text-indigo-700">YA</a>


      <div class="flex gap-4 max-lg:ml-auto">

        <RouterLink to="/chat" class="px-5 py-2.5 text-base rounded-full font-medium text-white bg-indigo-600 hover:bg-indigo-700 transition-all">
          Try Free
        </RouterLink>
      </div>
    </div>
  </header>

  <div class="px-4 sm:px-10 lg:py-16 py-10">
    <div class="max-w-screen-xl mx-auto">
      <div class="max-w-4xl mx-auto text-center relative z-10">

        <h1 class="text-slate-900 md:text-5xl text-4xl font-bold mb-6 leading-tight">
          Learn Computer Science in <span class="text-indigo-600">Yorùbá</span> 🤖
        </h1>

        <p class="text-base text-slate-600 leading-relaxed">
          Ask any Computer Science question and get simple, clear explanations in Yorùbá.
          From programming to algorithms, YorubaAI makes tech learning easy and fun.
        </p>

        <!-- Search / Prompt box -->
        <div class="max-w-xl mx-auto mt-12">
          <div class="bg-gray-100 flex px-6 py-5 border border-gray-300 rounded-full overflow-hidden focus-within:border-indigo-600 focus-within:bg-white transition-all">
            <input type="text" v-model="inputRef"
              placeholder="Beere ibeere kan... e.g. 'What is recursion?'"
              class="w-full text-slate-900 outline-none text-base bg-transparent" />

              <button v-on:click="redirectUser()" class="bg-indigo-600 text-white py-2 px-4 rounded-full hover:font-semibold">Ask</button>
          </div>
            <p class="text-red-600" v-if="errorRef != ''" >{{ errorRef }}</p>
        </div>


        <div class="mt-12 flex items-center justify-center flex-wrap gap-4">
          <button class="px-5 py-2.5 text-base rounded-full font-medium text-white bg-indigo-600 hover:bg-indigo-700">
            Start Learning Now
          </button>
          <button class="px-5 py-2.5 text-base rounded-full font-medium text-slate-900 border border-indigo-600 hover:bg-indigo-100">
            See Example Questions
          </button>
        </div>

        <div class="mt-12 text-slate-600 text-base">
          Built for students, beginners, and curious minds 💡
        </div>

      </div>
    </div>
  </div>
</div>

</template>
