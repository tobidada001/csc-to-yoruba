<script setup>
import LoadSpinner from '@/components/LoadSpinner.vue'
import { onMounted, ref } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const messages = ref([])
const loading = ref(false)
const inputRef = ref('')




const askAI = async (question) => {
  loading.value = true

  try {
    const res = await fetch('https://devly1-csc-in-yoruba.hf.space/generate', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ message: question }),
    })

    const data = await res.json()

    messages.value.push({
      text: data.response,
      sender: 'ai',
    })
  } catch (error) {
    messages.value.push({
      text: 'Something went wrong 😢',
      sender: 'ai',
    })
  }

  loading.value = false
}




const sendInputToModel = () => {
  const question = inputRef.value.trim()
  if (!question) return

  messages.value.push({ text: question, sender: 'user' })
  inputRef.value = ''

  askAI(question)
}



onMounted(() => {
  const searchQuery = route.query.search?.trim()

  if (searchQuery) {
    messages.value.push({ text: searchQuery, sender: 'user' })
    askAI(searchQuery)
  }
})


</script>

<template>
  <section class="bg-white py-16 px-4 sm:px-10">
    <div class="max-w-4xl mx-auto">
      <!-- Chat container -->
      <div class="bg-gray-50 border border-gray-200 rounded-3xl shadow-sm flex flex-col h-[600px]">
        <!-- Header -->
        <div class="px-6 py-4 border-b bg-white rounded-t-3xl">
          <h2 class="font-semibold text-lg text-slate-800">YorubaAI Assistant</h2>
          <p class="text-sm text-slate-500">Ask any Computer Science question</p>
        </div>

        <!-- Messages area -->
        <div id="chatMessages" class="flex-1 overflow-y-auto p-6 space-y-6">
          <!-- AI welcome message -->
          <div class="flex items-start gap-3">
            <div
              class="bg-indigo-600 text-white w-8 h-8 rounded-full flex items-center justify-center text-sm font-bold"
            >
              AI
            </div>
            <div
              class="bg-white border border-gray-200 rounded-2xl px-5 py-3 max-w-lg text-slate-700"
            >
              Hello 👋 Ask me CS questions and get answers in Yorùbá.
            </div>
          </div>

          <!-- Example user message -->
          <div
            v-for="(message, i) in messages"
            :key="i"
            class="flex items-start gap-3 w-full"
            :class="message.sender === 'user' ? 'justify-end' : 'justify-start'"
          >
            <!-- AI Avatar (only show for AI messages) -->
            <div
              v-if="message.sender === 'ai'"
              class="bg-indigo-600 text-white w-8 h-8 rounded-full flex items-center justify-center text-sm font-bold"
            >
              AI
            </div>

            <!-- Chat Bubble -->
            <div
              class="rounded-2xl px-5 py-3 max-w-lg"
              :class="
                message.sender === 'user'
                  ? 'bg-indigo-600 text-white'
                  : 'bg-white border border-gray-200 text-slate-700'
              "
            >
              {{ message.text }}
            </div>
          </div>



          <LoadSpinner v-if="loading" />
        </div>

        <!-- Input area -->
        <div class="p-4 border-t bg-white rounded-b-3xl">
          <div
            class="flex gap-3 bg-gray-100 border border-gray-300 rounded-full px-4 py-3 focus-within:border-indigo-600"
          >
            <input
              id="userInput"
              v-model="inputRef"
              type="text"
              placeholder="Type your question here... E.g. what is memory"
              class="flex-1 bg-transparent outline-none text-slate-700"
            />

            <button
              id="sendBtn"
              v-on:click="sendInputToModel()"
              class="bg-indigo-600 hover:bg-indigo-700 text-white px-6 py-2 rounded-full font-medium"
            >
              Send
            </button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
