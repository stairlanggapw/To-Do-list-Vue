<script setup>
import { ref } from 'vue'
import { PlusCircleIcon } from 'lucide-vue-next'
import {
  ClipboardList,
  ClipboardPen,
  ClipboardCheck,
  CheckCircle2,
  Trash2
} from 'lucide-vue-next'

const taskInput = ref('')
const tasks = ref([])

const addTask = () => {
  if (taskInput.value.trim() !== '') {
    tasks.value.push({
      id: Date.now(),
      title: taskInput.value,
      completed: false
    })
    taskInput.value = ''
  }
}

const completeTask = (taskId) => {
  const task = tasks.value.find((t) => t.id === taskId)
  if (task) {
    task.completed = !task.completed
  }
}

const deleteTask = (taskId) => {
  tasks.value = tasks.value.filter((t) => t.id !== taskId)
}

</script>

<template>
  <section class="flex justify-center items-center min-h-screen">
    <div class="bg-white rounded-2xl shadow-lg p-8 w-[600px]">
      <h1 class="text-3xl font-bold text-blue-900">
        Welcome to Your To-Do! 👋
      </h1>

      <p class="mt-2 text-gray-600">
        add your to-do list
      </p>

      <div class="flex items-center mt-6">
        <input
          v-model="taskInput"
          @keyup.enter="addTask"
          type="text"
          placeholder="Add a new task..."
          class="flex-1 p-3 rounded-lg border border-gray-300 focus:outline-none focus:ring-2 focus:ring-blue-500"
        />

        <button
          @click="addTask"
          class="ml-2 p-3 bg-blue-500 text-white rounded-lg hover:bg-blue-600 transition"
        >
          <PlusCircleIcon class="w-5 h-5" />
        </button>
      </div>

      <div class="flex justify-center items-center gap-15 mt-10">
        <div>
          <div class="border border-3 border-green-300 rounded-full p-2 hover:bg-green-100 transition cursor-pointer">
            <ClipboardList class="w-10 h-10 text-green-500" />
          </div>
          <p class="text-center">To-Do</p>
        </div>
        <div>
          <div class="border border-3 border-yellow-300 rounded-full p-2 hover:bg-yellow-100 transition cursor-pointer">
            <ClipboardPen class="w-10 h-10 text-yellow-500" />
          </div>
          <p class="text-center">Progress</p>
        </div>
        <div>
          <div class="border border-3 border-blue-300 rounded-full p-2 hover:bg-blue-100 transition cursor-pointer">
            <ClipboardCheck class="w-10 h-10 text-blue-500" />
          </div>
          <p class="text-center">Done</p>
        </div>
      </div>

      <div class="flex items-center justify-between mt-10">
        <h1 class="font-semibold text-xl text-blue-900">
          You're Tasks Here
        </h1>

        <p class="text-gray-400 cursor-pointer hover:text-blue-700">
          See All
        </p>
      </div>
      <div class="w-full h-px bg-blue-900 mt-3"></div>

      <div class="mt-5 bg-blue-100 rounded-xl p-4 h-[30vh] overflow-y-auto">

        <div
          v-if="tasks.length === 0"
          class="flex justify-center items-center h-full"
        >
          <h3 class="text-gray-400">
            Nothing To Do
          </h3>
        </div>

        <div
          v-else
          class="space-y-3"
        >

          <div
            v-for="task in tasks"
            :key="task.id"
            class="bg-white rounded-xl shadow p-4 flex justify-between items-center"
          >

            <h3
              class="text-lg font-medium text-center text-blue-900"
              :class="{ 'line-through text-gray-400': task.completed }"
            >
              {{ task.title }}
            </h3>

            <div class="flex gap-2">
              <button
                @click="completeTask(task.id)"
                class="bg-green-500 hover:bg-green-600 text-white p-2 rounded-full"
              >
                <CheckCircle2 class="w-5 h-5"/>
              </button>

              <button
                @click="deleteTask(task.id)"
                class="bg-red-500 hover:bg-red-600 text-white p-2 rounded-full"
              >
                <Trash2 class="w-5 h-5"/>
              </button>
            </div>

          </div>

        </div>

      </div>
    </div>
  </section>
</template>