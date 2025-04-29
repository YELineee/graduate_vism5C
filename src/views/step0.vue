<template>
   <div class="w-full h-full px-6 text-lg space-y-6 ">
      <div class="">
         <h1 class="text-3xl font-extrabold text-gray-800">Welcome to visM5c!</h1>
         <p class="text-base text-gray-500 mt-2 mb-10">
            A web-based platform for predicting and visualizing RNA m5C methylation sites from sequencing data.
         </p>
      </div>
      <div class="space-y-4 text-base">
         <div class="bg-gray-100 p-2 rounded-lg shadow">
            <h2 class="text-xl font-semibold text-gray-700">1.Configure Parameters</h2>
            <p class="text-gray-600"> Select the organism and set the false positive rate threshold for your analysis.
            </p>
         </div>
         <div class="bg-gray-100 p-2 rounded-lg shadow">
            <h2 class="text-xl font-semibold text-gray-700">2. Submit Your Data</h2>
            <p class="text-gray-600">
               Paste your RNA sequence (FASTA format) or upload a file in the input box below.
            </p>
         </div>
         <div class="bg-gray-100 p-2 rounded-lg shadow">
            <h2 class="text-xl font-semibold text-gray-700">3. View Results</h2>
            <p class="text-gray-600"> Predictions will be displayed instantly, including m5C site locations and
               confidence scores.</p>
         </div>
      </div>
   </div>
</template>