<script setup>
import { ref, watch } from 'vue';
import axios from 'axios';
import { StreamBarcodeReader } from 'vue-barcode-reader';

const search = ref('')
const products = ref([])

watch(
    () => search.value,
    async (newValue, oldValue) => {
        console.log(`${newValue} ${oldValue}`)
        await axios.get(`http://localhost:3050/api/v1/product/search/${newValue}`)
            .then((res) => {
                console.log(res.data);
                products.value = res.data.rows
            }).catch(error => {

            });
    }
)

const onDecode = (text) => {
    search.value = text;
};

const onLoaded = () => {
    console.log("loaded");
};
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
                <div>
                    <div class="relative">
                        <input type="text" class="w-full pl-4 pr-4 py-2 border rounded-lg" placeholder="search"
                            v-model="search" />
                        <div class="absolute inset-y-0 right-5 pl-3 flex items-center pointer-events-none z-50">
                            <span role="button" class="cursor-pointer">
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
  <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 4.875c0-.621.504-1.125 1.125-1.125h4.5c.621 0 1.125.504 1.125 1.125v4.5c0 .621-.504 1.125-1.125 1.125h-4.5A1.125 1.125 0 0 1 3.75 9.375v-4.5ZM3.75 14.625c0-.621.504-1.125 1.125-1.125h4.5c.621 0 1.125.504 1.125 1.125v4.5c0 .621-.504 1.125-1.125 1.125h-4.5a1.125 1.125 0 0 1-1.125-1.125v-4.5ZM13.5 4.875c0-.621.504-1.125 1.125-1.125h4.5c.621 0 1.125.504 1.125 1.125v4.5c0 .621-.504 1.125-1.125 1.125h-4.5A1.125 1.125 0 0 1 13.5 9.375v-4.5Z" />
  <path stroke-linecap="round" stroke-linejoin="round" d="M6.75 6.75h.75v.75h-.75v-.75ZM6.75 16.5h.75v.75h-.75v-.75ZM16.5 6.75h.75v.75h-.75v-.75ZM13.5 13.5h.75v.75h-.75v-.75ZM13.5 19.5h.75v.75h-.75v-.75ZM19.5 13.5h.75v.75h-.75v-.75ZM19.5 19.5h.75v.75h-.75v-.75ZM16.5 16.5h.75v.75h-.75v-.75Z" />
</svg></span>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <StreamBarcodeReader @decode="onDecode" @loaded="onLoaded" class="mb-3" style="width: 400px"
            v-if="search === 'abc'"></StreamBarcodeReader>
        {{ products }}
    </section>
</template>