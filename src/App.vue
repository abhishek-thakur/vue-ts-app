<template>
  <div>
    <button @click="handleClick('title')">Order By Title</button>
    <button @click="handleClick('salary')">Order By Salary</button>
    <button @click="handleClick('location')">Order By location</button>
    <jobs-list :jobs="jobs" :order="order"></jobs-list>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import JobsList from './components/JobsList.vue'
import Job from './types/Job'
import OrderTerm from './types/OrderTerm'

export default defineComponent({
  name: 'App',
  components: {
    JobsList
  },
  setup(){
    const jobs = ref<Job[]>([
      {title:'worker', location: 'amravati', salary: 20000, id:'1'},
      {title:'manager', location: 'pune', salary: 50000, id:'2'},
      {title:'developer', location: 'amravati', salary: 30000, id:'3'},
      {title:'CEO', location: 'mumbai', salary: 100000, id:'4'}
    ])

    const order = ref<OrderTerm>('title')
    const handleClick = (term: OrderTerm)=>{
      order.value = term
    }
    return {jobs, handleClick, order}
  }
  
});
</script>

