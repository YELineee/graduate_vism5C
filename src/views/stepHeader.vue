<template>
   <div class="flex items-center gap-2 p-5 pb-6">
      <navIcon class="h-8 w-8" v-if="iconType === 'nav'" />
      <paraIcon class="h-8 w-8" v-else-if="iconType === 'para'" />
      <dataIcon class="h-10 w-10" v-else-if="iconType === 'data'" />
      <resultIcon class="h-8 w-8" v-else-if="iconType === 'result'" />
      <span class="text-xs font-normal px-2 py-0 border rounded-full text-gray-600">{{ iconContent }}</span>
   </div>
</template>

<script setup>
import navIcon from '@/assets/navIcon.vue';
import paraIcon from '@/assets/paraIcon.vue';
import dataIcon from '@/assets/dataIcon.vue';
import resultIcon from '@/assets/resultIcon.vue';

defineProps({
   iconType: {
      type: String,
      default: false
   },
   iconContent: {
      type: String,
      default: 'Introduction'
   }
});   
</script>