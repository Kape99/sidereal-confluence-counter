<script setup>
import { ref } from 'vue'

const props = defineProps({
    resource: Text,
    count: Number
})
</script>


<template>
    <div class="card mb-3 text-center">
        <div class="row">
            <div class="col">
                <h1>{{ resource }}</h1>
            </div>
        </div>
        <div class="row">
            <div class="d-grid gap-2 col-2 mb-2">
                <button type="button" class="btn btn-primary" @click="$emit('decrementByTen')">-10</button>
            </div>
            <div class="d-grid gap-2 col-3 mb-2">
                <button class="btn btn-primary" type="button" @click="$emit('decrement')">-</button>
            </div>
            <div class="col">
                <h1>{{ count }}</h1>
            </div>
            <div class="d-grid gap-2 col-3 mb-2">
                <button type="button" class="btn btn-primary" @click="$emit('increment')">+</button>
            </div>
            <div class="d-grid gap-2 col-2 mb-2">
                <button type="button" class="btn btn-primary" @click="$emit('incrementByTen')">+10</button>
            </div>
        </div>
    </div>
</template>