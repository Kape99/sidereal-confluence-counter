<script setup>
import { computed, ref } from 'vue';
import ResourceCounter from './components/ResourceCounter.vue';


const totalScore = computed(() => {
  return resources.value.reduce((accumulator, resource) => accumulator += Math.floor((resource.count * resource.convertionRate) / 12), 0)
})

const remainderText = computed(() => {
  let remainderScore = resources.value.reduce((accumulator, resource) => accumulator += ((resource.count * resource.convertionRate) % 12), 0)
  if (remainderScore == 0) {
    return ""
  } else {
    return remainderScore + "/12"
  }
})

let id = 0
const resources = ref([
  { id: id++, resourceName: 'Victory Points', convertionRate: 12, count: 0 },
  { id: id++, resourceName: 'Octagons', convertionRate: 6, count: 0 },
  { id: id++, resourceName: 'Small Cubes', convertionRate: 3, count: 0 },
  { id: id++, resourceName: 'Large Cubes', convertionRate: 2, count: 0 },
  { id: id++, resourceName: 'Spaceships', convertionRate: 2, count: 0 },
])
</script>

<template>
  <h1>Total Score: {{ totalScore }} {{ remainderText }}</h1>
  <ul>

    <li v-for="resource in resources" :key="resource.id">
      <ResourceCounter @increment="resource.count++" @decrement="resource.count--" :resource="resource.resourceName"
        :count="resource.count">
      </ResourceCounter>

    </li>
  </ul>
</template>
