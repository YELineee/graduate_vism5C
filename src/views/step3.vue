<template>
   <div class="w-full h-full px-5 text-1xl">
      <div class="text-3xl text-gray-800 pb-10">
         <h2 class="font-extrabold">
            Results
         </h2>
         <p class="text-base text-gray-500 mt-2">
            Here are the results of your analysis.
         </p>
      </div>

      <div class="overflow-scroll h-10/12" style="overflow-x: hidden;">
         <div v-if="isLoading" class="flex justify-center items-center h-full">
            <!-- <el-loading /> -->
         </div>


         <!-- <div v-else-if="groupedData.length" v-for="(siteData, index) in groupedData" :key="index" class="mb-8">
            <h3 class="text-xl font-bold mb-2">{{ siteData.site }}</h3>
            <el-table :data="siteData.values" style="width: 100%">
               <el-table-column prop="value" label="Position" />
               <el-table-column prop="score" label="Score" />
            </el-table>
         </div> -->


         <div v-else class="text-gray-500 text-center mt-8">
            No data available
         </div>
      </div>

   </div>
</template>

<script setup>
import { computed } from 'vue';



</script>
