<template>
    <div class="job">
        <h2 class="job__title job__item">{{ job.title }}</h2>
        <p class="job__location job__item">Город: {{ job.location }}</p>
        <p class="job__salary job__item">Зарплата: {{ job.salary }}р.</p>
    </div>
</template>
<script lang="ts">
import Job from '@/interfaces/Job';
import { PropType, defineComponent } from 'vue';

export default defineComponent({
    name: 'JobsCard',
    components: {},
    props: {
        job: {
            required: true,
            type: Object as PropType<Job>
        }
    },
})
</script>
<style scoped>
    .job{
        max-width: 1160px;
        display: flex;
        flex-direction: column;
        gap:10px;
        background-color: #fff;
        padding: 15px;
        border-radius: 10px;
    }
    .job__item {
        margin: 0;
        padding: 0;
        font-size: 16px;
    }
    .job__title{
        font-size: 20px;
    }
</style>