<template>
  <div class="body">
    <div class="flex">
      <button @click="OrderJobs('location')">Order by Location</button>
      <button @click="OrderJobs('salary')">Order by Salary</button>
      <button @click="OrderJobs('title')">Order by Title</button>
    </div>
    <JobList :jobs="Jobs"  :order="order"/>
  </div>
</template>

<script lang="ts" setup>
import Job from "./types/Jobs"
import JobList from './components/JobList.vue'
import { ref, computed } from 'vue';

type OrderTerm = 'location' | 'salary' | 'title';

const order = ref<OrderTerm>('title');
const Jobs = ref<Job[]>([
  { id: 1, salary: 125.40, location: "Ogundawe Osibo", title: "Farm work" },
  { id: 2, salary: 150.80, location: "Babs Osibo", title: "Flute Player" },
  { id: 3, salary: 135.30, location: "Babs Lagos", title: "Tailor" },
  { id: 4, salary: 157.40, location: "Kubwa Abuja", title: "Frontend developer" },
]);


const OrderJobs = (term: OrderTerm) => {
  order.value = term
  Jobs.value = [...Jobs.value].sort((a, b) => {
    if (term === 'salary') {
      return a.salary - b.salary; 
    } else if (term === 'location') {
      return a.location.localeCompare(b.location); 
    } else if (term === 'title') {
      return a.title.localeCompare(b.title); 
    }
    return 0;
     });

};
</script>

<style>
.body {
  width: 100%;
  height: 100%;
  padding: 2rem;
}
.flex {
  display: flex;
  gap: 10px;
}
</style>
