<template>
   <div class="w-full h-full bg-white border-0.5 rounded-2xl shadow-xs border-[1px] border-gray-200"
      :style="{ boxShadow: isHovered ? '0px 4px 8px rgba(0, 0, 0, 0.3)' : 'none', transition: 'box-shadow 0.5s ease-in-out' }">
      <div class="w-full h-1/12">
         <slot name="header"></slot>
      </div>
      <div class="w-full h-9/12">
         <slot name="content"></slot>
      </div>
      <div class="w-full h-2/12 flex items-center justify-center rounded-2xl relative select-none">
         <div class="text-5xl absolute bottom-0 left-0 px-1"
            :class="{ 'text-gradient': isHovered, 'text-gray-300': !isHovered }">
            {{ stepName }}
         </div>
      </div>
   </div>
</template>

<script setup>
defineProps({
   isHovered: {
      type: Boolean,
      default: false
   },
   stepName: {
      type: String,
      required: true
   }
});
</script>

<style scoped>
.text-gradient {
   animation: textAnimate 1s ease-in-out;
   color: #161516;
   /* Ensure the color stays after the animation ends */
}

@keyframes textAnimate {
   0% {
      color: #d1d5dc;
   }

   100% {
      color: #161516;
   }
}

.test {
   margin: 0;

   background-image:
      radial-gradient(#F9D2E1 40%, transparent 0),
      radial-gradient(#F9D2E1 40%, transparent 0);
   background-size: 15px 15px;
   background-position: 0 0, 30px 30px;

}
</style>
