<template>
  <div class="body">
    <JobList :jobs="Jobs"/>
  </div>
</template>

<script lang="ts" setup>
import Job from "./types/Jobs"
import JobList from './components/JobList.vue'
import { ref } from 'vue';
// let name = ref<number | string>('Marvelous')
// const changeName = (newVal: string | number) => {
//   name.value = newVal
// }
const Jobs = ref<Job[]>([
  { id: 1, salary: 125.40, location: "Ogundawe Osibo", title: "Farm work" },
  { id: 2, salary: 150.80, location: "Babs Osibo", title: "Flute Player" },
  { id: 3, salary: 135.30, location: "Babs Lagos", title: "Tailor" },
  { id: 4, salary: 157.40, location: "Kubwa Abuja", title: "Frontend developer" }
  
  ])
 
</script>

<style>
.body{
  width: 100%;
  height: 100%;
  padding: 2rem;
}
</style>
