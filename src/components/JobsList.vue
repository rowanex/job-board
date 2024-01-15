<template>
    <div class="sort-res">
        <p>SORTED BY {{ sortType.toUpperCase() }}</p>
    </div>
    <transition-group name="list" tag="div" class="jobs">
        <JobsCard v-for="job in jobs" :job="job" :key="job.id"/>
    </transition-group>
</template>
<script lang="ts">
import { PropType, defineComponent } from 'vue';
import Job from '@/interfaces/Job';
import JobsCard from './JobsCard.vue';

export default defineComponent({
    name: 'JobsList',
    components: {JobsCard},
    props: {
        jobs: {
            required: true,
            type: Array as PropType<Job[]>
        },
        sortType: {
            required: true,
            type: String
        }
    },
})
</script>
<style scoped>
    .jobs {
        display: flex;
        flex-direction: column;
        gap: 40px;
    }
    .list-move {
        transition: all 0.5s;
    }
</style>