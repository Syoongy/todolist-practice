<template>
  <main>
    <div class="bg-gray-50">
      <div
        class="max-w-screen-xl px-4 py-12 mx-auto sm:px-6 lg:py-16 lg:px-8 lg:flex lg:items-center lg:justify-between"
      >
        <h2
          class="text-3xl font-extrabold leading-9 tracking-tight text-gray-900 sm:text-4xl sm:leading-10"
        >
          Ready to dive in?
          <br />
          <span class="text-indigo-600">Vite 2.x + Vue 3.x + Tailwind 2.x</span>
        </h2>
        <div class="flex mt-8 lg:flex-shrink-0 lg:mt-0">
          <div class="inline-flex rounded-md shadow">
            <router-link
              to="/about"
              class="inline-flex items-center justify-center px-5 py-3 text-base font-medium leading-6 text-white transition duration-150 ease-in-out bg-indigo-600 border border-transparent rounded-md hover:bg-indigo-500 focus:outline-none"
            >
              Next Page
            </router-link>
          </div>
          <ButtonRepo />
        </div>
      </div>
    </div>
    <div class="container m-8 mx-auto">
      <p class="text-center text-xl">{{ exampleMutableString }}</p>
      <div class="mb-4 mt-6">
        <label
          class="block text-gray-700 text-sm font-semibold mb-2"
          for="inputField"
        >
          New text value
        </label>
        <input
          class="text-sm appearance-none rounded w-full py-2 px-3 text-gray-700 bg-gray-200 leading-tight border-none focus:outline-none focus:ring-blue-300 focus:ring-4 h-10"
          name="inputField"
          type="text"
          v-model="exampleMutableString"
        />
      </div>

      <p class="text-center text-xl">You can trigger functions like this too</p>
      <div class="inline-block mr-2 mt-2 w-full">
        <button
          type="button"
          class="focus:outline-none text-white text-sm py-2.5 px-5 rounded-md bg-blue-500 hover:bg-blue-600 hover:shadow-lg w-full"
          @click="changeStringText"
        >
          Change text to 'Hello World'
        </button>
      </div>
    </div>
  </main>
</template>

<script setup>
import { ref } from "vue";
import ButtonRepo from "@/components/ButtonRepo.vue";

const exampleMutableString = ref(
  "This is a string that can have it's value changed"
);

const changeStringText = () => {
  exampleMutableString.value = "Hello World"
}
</script>