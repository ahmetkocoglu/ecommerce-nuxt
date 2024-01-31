<script setup>
import { ref, watch } from 'vue';

const search = ref('')

watch(
  () => search.value,
  (sum, abc) => {
    console.log(`${sum} ${abc}`)
  }
)
</script>
<template>
    <section class="bg-white dark:bg-gray-900">
        <div class="py-8 lg:py-16 px-4 mx-auto max-w-screen-md">
            <h2 class="mb-4 text-4xl tracking-tight font-extrabold text-center text-gray-900 dark:text-white">New Product
            </h2>
            <p class="mb-8 lg:mb-16 font-light text-center text-gray-500 dark:text-gray-400 sm:text-xl">New Product</p>
            <div>
                <label for="title" class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300">Product
                    Title</label>
                <input type="text" id="title"
                    class="shadow-sm bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-primary-500 focus:border-primary-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-primary-500 dark:focus:border-primary-500 dark:shadow-sm-light"
                    placeholder="Product title" required v-model="search">
            </div>
            {{ search }}
        </div>
    </section>
</template>