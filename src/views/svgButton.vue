<template>
   <div
      class="cursor-pointer w-16 h-16 flex items-center justify-center hover:scale-110 transition-transform duration-300"
      @click="$emit('click')">
      <arrow v-if="!isExpand" class="w-10 h-10" />
      <cross v-if="isExpand" class=" w-10 h-10" />
   </div>
</template>

<script setup>
import arrow from '@/assets/arrowIcon.vue';
import cross from '@/assets/crossIcon.vue';

defineProps({
   isExpand: {
      type: Boolean,
      default: false
   },
   isAnimating: {
      type: Boolean,
      default: false
   }
});

defineEmits(['click']);
</script>
