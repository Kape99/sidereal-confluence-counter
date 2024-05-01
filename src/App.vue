<script setup>
import { computed, ref } from 'vue';
import ResourceCounter from './components/ResourceCounter.vue';


const totalScore = computed(() => {
  const total = resources.value.reduce((accumulator, resource) => accumulator += ((resource.count * resource.convertionRate)), 0)
  const integralPart = Math.floor(total / 12);
  return integralPart;
})

const remainderText = computed(() => {
  const total = resources.value.reduce((accumulator, resource) => accumulator += ((resource.count * resource.convertionRate)), 0)
  const remainderScore = total % 12;
  if (remainderScore == 0) {
    return ""
  } else {
    return remainderScore + "/12"
  }
})

let id = 0
const resources = ref([
  { id: id++, resourceName: 'Victory points', convertionRate: 12, count: 0 },
  { id: id++, resourceName: 'Octagons', convertionRate: 6, count: 0 },
  { id: id++, resourceName: 'Large cubes', convertionRate: 3, count: 0 },
  { id: id++, resourceName: 'Small cubes', convertionRate: 2, count: 0 },
  { id: id++, resourceName: 'Spaceships', convertionRate: 2, count: 0 },
])

function increment(res) {
  res.count++;
}

function decrement(res) {
  if (res.count != 0) {
    res.count--;
  }
}

function incrementByTen(res) {
  res.count += 10;
}

function decrementByTen(res) {
  if (res.count > 10) {
    res.count -= 10;
  }
  else {
    res.count = 0;
  }
}

</script>

<template>
  <h1>Total Score: {{ totalScore }} {{ remainderText }}</h1>
  <div class="container">

    <div class="row" v-for="resource in resources" :key="resource.id">
      <ResourceCounter @increment="increment(resource)" @decrement="decrement(resource)"
        @incrementByTen="incrementByTen(resource)" @decrementByTen="decrementByTen(resource)"
        :resource="resource.resourceName" :count="resource.count">
      </ResourceCounter>
    </div>
  </div>
</template>
