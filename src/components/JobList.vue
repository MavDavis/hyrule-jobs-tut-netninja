<template>
    <div class="joblist">
        <button @click="OrderJobs()">Order by location</button>
        <button @click="OrderJobs()">Order by Salary</button>
        <button @click="OrderJobs()">Order by Title</button>
        <transition-group name="move" tag="ul">
            <li v-for="job in jobs" :key="job.id" class="job-card">
          <h2> {{ job.title }} in {{ job.location }} </h2>
          <div class="salary">
            <p>$ {{ job.salary }}</p>
          </div>
          <div class="description">
            <p>
              Lorem ipsum dolor sit, amet consectetur adipisicing elit. Maxime
              perspiciatis qui sapiente rerum? Cupiditate, nemo veritatis cum esse
              praesentium quidem maiores facere iste. Consectetur eligendi autem neque,
              dolorem cumque dolorum!
            </p>
          </div>
        </li>
    </transition-group>
</div>
  </template>
  
  <script setup lang="ts">
  import Job from '@/types/Jobs';
  import { defineProps, PropType } from 'vue';
  
  const props = defineProps({
    jobs: {
      type: Array as PropType<Job[]>,
      required: true,
    },
  });
  type OrderTerm = 'location' | "salary" | "title"
  const OrderJobs = (term : OrderTerm)=>{
    return term
  }
  </script>
  
  <style scoped>
  .joblist {
    padding: 0;
    margin: 0;
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 20px;
  }
  
  .job-card {
    background-color: #ffefe6;
    width: 100%;
    border-radius: 10px;
    box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1);
    padding: 20px;
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
  }
  
  .job-card h2 {
    font-size: 1.5rem;
    margin: 0;
  }
  
  .salary {
    font-weight: bold;
    color: #b03a2e; 
  }
  
  .description p {
    font-size: 0.9rem;
    line-height: 1.5;
    color: #333;
  }
.move-enter-active, .move-leave-active {
  transition: all 0.5s ease; 
}
.move-enter, .move-leave-to  {
  position: absolute; 
  opacity: 0; 
}
  @media (max-width: 768px) {
    .job-card {
      padding: 15px;
    }
  }
  </style>
  