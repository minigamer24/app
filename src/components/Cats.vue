<script setup>
    import { ref } from 'vue'
    import monkey from './cats.json'
    import Cat from './cat.vue'
    defineProps({
        jesus: String
    }) 
   

    let imgSrc = ref(null)

    const showImage = url => imgSrc.value = url

</script> 
<template>
    <button @click="showImage(null)"> Close </button>
    <div v-if="imgSrc != null">
        <Cat :dogs="imgSrc" />
        <!-- <img :src="imgSrc"> -->
    </div>
    <div v-if="imgSrc == null" v-for="x of monkey" @click="() => showImage(x)">
        <Cat :dogs="x" />
    </div>

    {{ monkey[0].url }}
    {{ jesus }}
    <!-- <Cat msg="fish"/> -->
</template>

<style>
</style>
