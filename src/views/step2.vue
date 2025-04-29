<template>
   <div class="w-full h-full px-5">
      <!-- up -->
      <div class="w-full h-10/12 ">
         <div class="text-3xl text-gray-800 pb-10">
            <h2 class="font-extrabold">
               Input RNA Sequence
            </h2>
            <p class="text-base text-gray-500 mt-2">
               Paste your sequence in FASTA format (e.g., `>seq1\nATGGCA...`) or upload a file:
            </p>
         </div>
         <div class="w-full h-8/12 border border-gray-300 rounded" :class="{ 'border-blue-500 border-2': isDragging }"
            @dragover.prevent="handleDragOver" @dragleave="handleDragLeave" @drop.prevent="handleDrop">
            <textarea class="w-full h-full p-2 outline-none resize-none" placeholder="Enter text here"
               v-model="inputText" @input="handleInput"></textarea>
         </div>
      </div>
      <!-- botton -->
      <div class="w-full h-2/12 rounded-xl pt-2">
         <div>
            <!-- <button @click="sendRequest"  -->
            <button @dblclick="sendRequest" @click="getExample" class="bg-black text-white font-bold py-2 px-4 rounded shadow-md transition duration-300 ease-in-out
               transform hover:scale-105 mr-5">
               Submit
            </button>

            <!-- <el-button @click="sendRequest" type="primary" plain>Primary</el-button> -->
         </div>
      </div>
   </div>
</template>

<script setup>
import { ref } from 'vue';


const isDragging = ref(false);
const inputText = ref('');

function handleInput() {
   console.log('inputText:', inputText.value);
}

function handleDragOver() {
   isDragging.value = true;
}

function handleDragLeave() {
   isDragging.value = false;
}

function handleDrop(event) {
   isDragging.value = false;
   const files = event.dataTransfer?.files;
   if (files && files.length > 0) {
      Array.from(files).forEach(file => {
         if (file.type.startsWith('image/')) {
            console.log('Dropped file:', file.name);
         } else {
            console.warn('Unsupported file type:', file.type);
         }
      });
   } else {
      console.warn('No files detected in drop event.');
   }
}

const getExample = () => {
   inputText.value = '>seq0\nGGAGCGCGCCTGACCCAGGGCGCACCGTGGGACCCGGGCGCGGGGCTGGCGAAGAGCTGCCCCGCGGGGCTAGCAGCCGCGGAGTGGCCTACAGGGGTCCTCCCCCGGAGGGGCCGGGCCGGGGCGGGGAGATGAACGGCTTCAGCACAGAGGAGGACAGCCGCGAAGGGCCCCCTGCCGCCCCCGCCGCCGCCCCGGGCTACGGCCAGAGCTGCTGCCTCATCGCGGACGGCGAGCGCTGCGTCCGGCCCGCGGGCAACGCCTCCTTCAGCAAGAGGGTGCAGAAAAGCATCTCGCAGAAGAAACTCAAGCTGGACATAGACAAGAGCGTAAGGCACCTGTATATCTGCGACTTCCACAAAAATTTCATCCAGAGCGTCCGAAATAAAAGGAAGAGGAAGGCAAGTGACGATGGCGGAGACTCCCCCGAGCACGATGCTGACATC';
   console.log('inputText:', inputText.value);
};

</script>
