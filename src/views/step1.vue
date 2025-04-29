<template>
   <div class="w-full h-full items-center px-6 text-1xl ">
      <div class="text-3xl text-gray-800 mb-10">
         <h2 class="font-extrabold">
            Configure Analysis
         </h2>
         <p class="text-base text-gray-500 mt-2">
            Set your parameters for metagenomic sequence analysis.
         </p>
      </div>
      <!-- Cell Type Selection -->
      <div>
         <p class="text-lg py-1">Select Species:</p>
         <div class="mb-10 w-full">
            <div class="grid grid-cols-2 w-full rounded-md overflow-hidden border border-gray-200">
               <button @click="cellType1 = 'mouse'" :class="[
                  'flex items-center justify-center gap-2 py-2 transition-colors',
                  cellType1 === 'mouse' ? 'bg-black text-white' : 'bg-gray-100 hover:bg-gray-200'
               ]">
                  <mouseIcon class="h-12 w-12" :color="cellType1 === 'mouse' ? '#ffffff' : '#000000'" />
                  <span>Mouse</span>
               </button>
               <button @click="cellType1 = 'human'" :class="[
                  'flex items-center justify-center gap-2 py-2 transition-colors',
                  cellType1 === 'human' ? 'bg-black text-white' : 'bg-gray-100 hover:bg-gray-200',
                  isDisabled ? 'opacity-50 cursor-not-allowed' : ''
               ]" :disabled="isDisabled">
                  <humanIcon class="h-12 w-12" :color="cellType1 === 'human' ? '#ffffff' : '#000000'" />
                  <span>Human</span>
               </button>
            </div>
         </div>
         <!-- False Positive Rate -->
         <div>
            <p class="text-lg py-1">Set False Positive Rate: </p>
            <div class="flex justify-between">
               <label class="text-sm font-medium">Threshold Value</label>
               <span class="text-sm text-gray-500">{{ predictionThreshold }}</span>
            </div>
            <div class="relative group">
               <input type="range" v-model="predictionThreshold" min="0.01" max="1" step="0.01"
                  class="w-full h-2 bg-gray-200 rounded-lg appearance-none cursor-pointer accent-black" />
            </div>
            <div class="flex justify-between text-xs text-gray-500">
               <span>0</span>
               <span>1</span>
            </div>
         </div>
      </div>
   </div>
</template>

<script setup>
import { ref } from 'vue'
import mouseIcon from '@/assets/mouseIcon.vue'
import humanIcon from '@/assets/humanIcon.vue'

const cellType1 = ref('mouse')
const isDisabled = ref(true)
const predictionThreshold = ref(0.5)
</script>
