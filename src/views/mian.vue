<template>
   <div class="w-screen h-screen roboto-condensed-400">
      <div class="h-2/12 w-full px-30 py-10 schibsted-grotesk-400 flex justify-between items-center">
         <div class="relative flex items-center">
            <img src="../assets/CSULogo.png" alt="logo" class=" mr-2 invert w-0" />
         </div>
         <div class="flex items-center">
            <p class="font-bold mr-4">
               <samp class="font-light italic"> From Vision to Reality by </samp>
               <samp class="text-lg">YELineee </samp>
            </p>
            <a href="https://github.com/YELineee">
               <githubIcon class="w-8 h-8" />
            </a>
         </div>
      </div>
      <div class="h-10/12 w-full flex justify-center ">
         <div class="w-10/12 h-10/12 flex flex-row relative">

            <!-- step1 -->
            <div id="step1" class="w-1/4 h-full p-0.5 z-10" @mouseover="hoverStep(1, true)"
               @mouseleave="hoverStep(1, false)">
               <CardContent :is-hovered="hoverStates.step1" step-name="0">
                  <template #header>
                     <stepHeader icon-type="nav" icon-content="Introduction" />
                  </template>
                  <template #content>
                     <step0 />
                  </template>
               </CardContent>
            </div>

            <!-- step2 -->
            <div id="step2" class="w-1/4 h-full p-0.5 z-20" @mouseover="hoverStep(2, true)"
               @mouseleave="hoverStep(2, false)">
               <CardContent :is-hovered="hoverStates.step2" step-name="1">
                  <template #header>
                     <stepHeader icon-type="para" icon-content="Parameters" />
                  </template>
                  <template #content>
                     <step1 />
                  </template>
               </CardContent>
            </div>

            <!-- step3 -->
            <div id="step3" class="w-1/4 h-full p-0.5 z-30" @mouseover="hoverStep(3, true)"
               @mouseleave="hoverStep(3, false)">
               <CardContent :is-hovered="hoverStates.step3" step-name="2">
                  <template #header>
                     <stepHeader icon-type="data" icon-content="Data" />
                  </template>
                  <template #content>
                     <step2 />
                  </template>
               </CardContent>
            </div>

            <!-- step4 -->
            <div id="step4" class="w-1/4 h-full absolute p-0.5 top-0 right-0 z-40" @mouseover="hoverStep(4, true)"
               @mouseleave="hoverStep(4, false)">
               <CardContent class="relative" :is-hovered="hoverStates.step4" step-name="3">
                  <template #header>
                     <stepHeader icon-type="result" icon-content="Result" />
                     <SvgButton class="absolute top-1 right-1 z-50" @click="toggleAnimation" :is-expand="isExpand" />
                  </template>
                  <template #content>
                     <step3 />
                  </template>
               </CardContent>
            </div>
         </div>
      </div>

   </div>
</template>

<script setup>
import anime from 'animejs';
import { compile, onMounted, ref, watch } from 'vue';
import CardContent from './cardContent.vue';
import SvgButton from './svgButton.vue';
import stepHeader from './stepHeader.vue';
import githubIcon from '@/assets/githubIcon.vue';
import step0 from './step0.vue';
import step1 from './step1.vue';
import step2 from './step2.vue';
import step3 from './step3.vue';



const isExpand = ref(false);
const isAnimating = ref(false);
const hoverStates = ref({
   step1: false,
   step2: false,
   step3: false,
   step4: false,
});
let timeline;

onMounted(() => {
   timeline = anime.timeline({
      easing: 'easeInOutQuad',
      duration: 500,
      autoplay: false,
      begin: () => {
         isAnimating.value = true;
      },
      complete: () => {
         timeline.reverse();
         isExpand.value = !isExpand.value;
         isAnimating.value = false;
         console.log('animation complete', isExpand.value);
      },
   });

   timeline
      .add({
         targets: '#step1',
         translateX: 0,
      })
      .add({
         targets: '#step2',
         translateX: "-75%",
      })
      .add({
         targets: '#step3',
         translateX: "-150%",
      })
      .add({
         targets: '#step4',
         width: '81.25%',
         translateX: 0,
         duration: 1000,
      });
});

const toggleAnimation = () => {
   if (timeline.progress > 0 && timeline.progress < 100) return;
   timeline.play();
};

const hoverStep = (step, isHovering) => {
   hoverStates.value[`step${step}`] = isHovering;
};

</script>
