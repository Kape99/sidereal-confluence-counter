<script setup>
import { ref } from 'vue'

const props = defineProps({
    resource: Text,
    count: Number
})

function increment() {
    count++;
}
function decrement() {
    if (count != 0)
        count--;
}
</script>


<template>
    <div>
        <button @click="$emit('increment')">+</button>
        <h1>{{ resource }} : {{ count }}</h1>
        <button @click="$emit('decrement')">-</button>
    </div>
</template>