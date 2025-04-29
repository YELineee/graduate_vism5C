<template>
   <div class="w-full h-screen flex flex-col">
      <!-- 添加导航栏 -->
      <nav
         class="w-full h-16 flex bg-zinc-300 items-center justify-between px-60 text-black schibsted-grotesk-400 pacifico-regular">
         <div class="text-xl font-bold h-full bg-gray-200 flex items-center justify-center px-10  ">
            Vism5c
         </div>
         <div>
            <a href="#" class="mx-2">链接1</a>
            <a href="#" class="mx-2">链接2</a>
         </div>
      </nav>

      <!-- 主内容区域 -->
      <div class="flex-1 flex justify-center items-center">
         <div class="flex flex-row w-11/12 h-10/12">
            <div class="w-full h-full basis-1/3">
               <dropData />
            </div>
            <div class="w-full h-full basis-2/3 bg-amber-600">02</div>
         </div>
      </div>
   </div>
</template>

<script setup>
import dropData from './dropData.vue';
</script>