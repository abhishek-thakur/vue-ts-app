<template>
    <div>
        <p>Ordered by {{order}}</p>
        <ul>
            <li v-for="job in orderedJobs" :key="job.id">
                <h2>{{job.title}} in {{job.location}}</h2>
                <div>
                    <p>{{job.salary}} rupees</p>
                </div>
                <div class="description">
                    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Minima alias consequatur laborum. In dolores eligendi, explicabo doloremque quis adipisci enim id unde hic et voluptatibus aliquid sit autem atque recusandae?</p>
                </div>
            </li>
        </ul>
    </div>
</template>
<script lang="ts">
import { computed, defineComponent, PropType } from 'vue'
import Job from '../types/Job'
import OrderTerm from '../types/OrderTerm'

export default defineComponent({
    props:{
        jobs:{
            required : true,
            type: Array as PropType<Job[]>
        },
        order :{
            required: true,
            type: String as PropType<OrderTerm>
        }
    },
    setup(props){
        const orderedJobs = computed(() =>{
            return [...props.jobs].sort((a: Job, b:Job)=>{
                return a[props.order]> b[props.order] ? 1 : -1
            })
        })
        return {orderedJobs}
    }
})
</script>
