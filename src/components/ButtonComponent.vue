<template>
<div class="card"  v-for="b in buttons">
            <h1 class="button-text">{{ props.title }}</h1>
            <div style="display: flex;">
            <img :src="b.image" style="width: 70px;">
            </div>
        </div>
</template>

<script setup lang="ts">

const props = defineProps({
   title: {
    type: String,
    default: "123"
   }
    
})
</script>
