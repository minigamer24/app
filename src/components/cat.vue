<script setup>
import { ref, onMounted } from 'vue'

let {dogs} = defineProps({
  dogs: Object,
})

let cursorX = ref(null)
let cursorY = ref(null)

const printMousePos = (e) => {
  console.log(e)
  cursorX.value = e.clientX
  cursorY.value = e.clientY
}
const beijing = async () => await fetch(`http://localhost:3000/fish/${cursorX.value}/${cursorY.value}/${dogs.url.replace(/(^\w+:|^)\/\//, '').replaceAll('/', '-')}`)
//.then((res) => res.json())

/* onMounted(async () => {
  console.log("DOGS", dogs)
  await beijing()
}) */
</script>

<template>
    <h1>{{ dogs.id }}</h1>
    {{ cursorX }} <br> 
    {{ cursorY }}
    <img :style="{'filter': `grayscale(${cursorX/20}%)`}" @mousedown="e => printMousePos(e)" id="fish" @click="beijing()" :src="`${dogs.url}`" alt="">
</template>
<style>
h1{ 
  color: #d40000;
}
</style>
