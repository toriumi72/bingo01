<script setup lang="ts">
const number = ref<number | null>(null)
const previousNumbers = reactive<number[]>([])

const generateNumber = () => {
  let generated: number
  do {
    generated = Math.floor(Math.random() * 75) + 1
  } while (previousNumbers.includes(generated))
  
  number.value = generated
  previousNumbers.push(generated)
}
</script>

<template>
  <div class="container mx-auto mt-10 text-center">
    <button @click="generateNumber" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-full">
      乱数を生成
    </button>
    <div v-if="number" class="selected-number mt-10 text-6xl font-bold">{{ number }}</div>
    <div class="previous-numbers mt-10 text-xl">
      選択済みの番号:
      <ul class="mt-5">
        <li v-for="num in previousNumbers" :key="num" class="inline-block mr-4">{{ num }}</li>
      </ul>
    </div>
  </div>
</template>

<style scoped>

</style>
