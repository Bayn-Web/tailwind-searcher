<template>
  <div class="w-full h-auto flex justify-center items-center">
    <div class="w-[200px] h-[200px] bg-slate-500" :class="formedClass">
      {{ formedClass }}</div>
    <div
      class="sm md lg xl 2xl aspect-auto aspect-square aspect-video mx-auto columns-1 box-border box-content float-right float-left float-none object-contain object-cover object-fill object-none object-scale-down object-left-top object-right object-right-bottom object-right-top object-top overflow-auto overflow-hidden overflow-clip overflow-x-hidden overscroll-auto overscroll-contain overscroll-none overscroll-y-auto static fixed absolute relative sticky flex grid inset-0 top-0 right-0 bottom-0 left-0 visible invisible z-0 basis-0 basis-1/2 flex-row flex-row-reverse flex-col flex-col-reverse flex-wrap flex-wrap-reverse flex-nowrap grow grow-0 shrink shrink-0 grid-cols-3 col-span-3 grid-rows-3 row-span-3 gap-0 gap-x-0 gap-y-0 justify-normal justify-start justify-end justify-center justify-between justify-around justify-evenly justify-items-start justify-items-end justify-items-center justify-items-stretch justify-self-auto justify-self-start justify-self-end justify-self-center justify-self-stretch content-normal content-center content-start content-end content-between content-around content-evenly content-baseline content-stretch items-start items-end items-center items-baseline items-stretch self-auto self-start self-end self-center self-stretch self-baseline place-content-center place-content-start place-content-end place-content-between place-content-around place-content-evenly place-content-baseline place-content-stretch place-items-start place-items-end place-items-center place-items-baseline place-items-stretch place-self-auto place-self-start place-self-end place-self-center place-self-stretch p-0 px-0 pr-0 pb-0 pl-0 m-0 mx-0 my-0 mt-0 mr-0 mb-0 ml-0 space-x-0 > * + * space-y-0 > * + * w-0 min-w-0 max-w-0 h-0 min-h-0 min-h-full min-h-screen min-h-fit min-h-min min-h-max max-h-0 font-sans font-serif font-mono text-xs text-sm text-base text-lg text-xl text-2xl italic not-italic font-thin font-extralight font-light font-normal font-medium font-semibold font-bold font-extrabold font-black tracking-tighter tracking-tight tracking-normal tracking-wide tracking-wider tracking-widest line-clamp-3 leading-3 list-inside list-outside list-none list-disc list-decimal text-left text-center text-right text-justify text-slate-300 decoration-solid decoration-double decoration-dotted decoration-dashed decoration-wavy decoration-2 uppercase lowercase capitalize indent-8 align-baseline align-top align-middle align-bottom whitespace-normal whitespace-nowrap whitespace-pre whitespace-pre-line content-none bg-clip-border bg-clip-padding bg-clip-content bg-clip-text bg-slate-300 bg-origin-border bg-origin-padding bg-origin-content bg-bottom bg-center bg-repeat bg-no-repeat bg-auto bg-cover bg-contain bg-none bg-gradient-to-t bg-gradient-to-tr from-neutral-400 via-neutral-200 to-neutral-600 rounded-sm rounded rounded-md rounded-lg rounded-xl rounded-full border-0 border border-2 border-slate-400 border-r-rose-950 border-solid border-dashed divide-x-2 divide-blue-400 divide-solid divide-dashed outline-none ring ring-slate-400 ring-offset-1 shadow-sm shadow shadow-md shadow-lg shadow-xl shadow-2xl shadow-inner shadow-slate-200 opacity-10 blur-sm brightness-105 contrast-125 drop-shadow-sm drop-shadow drop-shadow-md drop-shadow-lg drop-shadow-xl drop-shadow-2xl grayscale hue-rotate-15 invert saturate-150 sepia backdrop-blur-sm transition-all transition transition-colors transition-opacity transition-shadow transition-transform duration-75 ease-linear ease-in ease-out ease-in-out delay-75 animate-bounce animate-pulse animate-ping animate-spin scale-50 scale-x-50 rotate-45 translate-x-1 skew-x-6 origin-top origin-top-right accent-slate-400 appearance-none cursor-not-allowed cursor-none cursor-wait cursor-pointer cursor-default pointer-events-none resize-none scroll-smooth select-none hidden">
    </div>
  </div>
</template>

<script lang="ts" setup>
import {
  computed
} from 'vue';

const parentProps = defineProps<{ classNames: { label: string, value: string, id: number }[] }>()

const init = ''

const formedClass = computed(() => {
  return parentProps.classNames.reduce((last, current) => {
    return last + " " + current.label + " "
  }, init)
})
</script>

<style scoped></style>