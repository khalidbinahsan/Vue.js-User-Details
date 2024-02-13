<script setup>
import { reactive, ref } from 'vue'
const persons = reactive([
  { name: 'Khalid Bin Ahsan', age: 25, email: 'developer@khalidbinahsan.com' },
  { name: 'Wahidul', age: 24, email: 'wahidul@gmail.com' },
  { name: 'Musharraf', age: 29, email: 'musharraf@gmail.com' },
  { name: 'Muhid', age: 25, email: 'muhid@gmail.com' }
])
const activeIndex = ref();
</script>

<template>
  <section class="mx-auto container text-left max-w-[800px] pt-20">
    <h1 class="text-4xl mb-10 text-center font-bold">User Details</h1>
    <div class="flex">
      <div class="w-1/2 pr-10">
        <select class="block w-full rounded-md border-0 py-1.5 pl-2 pr-20 text-gray-900 ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6" v-model="activeIndex">
          <option disabled selected>Select a Person</option>
          <template v-for="(person, index) in persons" :key="index">
            <option :value="index">{{ person.name }}</option>
          </template>
        </select>
      </div>
      <div class="w-1/2 pl-10">
        <div class="mb-5" v-for="(value, key, index) in persons[activeIndex]" :key="index">
          <label :for="key" class="block text-sm font-medium leading-6 text-gray-900 capitalize">{{ key }}</label>
          <div class="relative mt-2 rounded-md shadow-sm">
            <input type="text" :name="key" :id="key" :value="value" v-model="persons[activeIndex][key]"
              class="block w-full rounded-md border-0 py-1.5 pl-7 pr-20 text-gray-900 ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6">
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped></style>
