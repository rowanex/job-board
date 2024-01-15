<template>
  <JobsHeader @sortBy="handleSortBy"/>
  <JobsList :jobs="sortedJobs" :sortType="sortType"/>
</template>

<script lang="ts">
import { computed, defineComponent, ref } from 'vue';
import Job from '@/interfaces/Job'
import JobsList from './components/JobsList.vue';
import JobsHeader from './components/JobsHeader.vue';
import SortingTerm from './types/SortingTerm';

export default defineComponent({
  name: 'App',
  components: {
    JobsList,
    JobsHeader
  },
  setup(){

    const jobs = ref<Job[]>([
      {id: 1, title: 'Фермер', location: 'Москва', salary: 30000},
      {id: 2, title: 'Эколог', location: 'Москва', salary: 40000},
      {id: 3, title: 'Психотерапевт', location: 'Москва', salary: 35000},
      {id: 4, title: 'Астрофизик', location: 'Екатеринбург', salary: 30000},
      {id: 5, title: 'Ветеринар', location: 'Екатеринбург', salary: 20000},
    ]);

    const sortType = ref<SortingTerm>('title');

    const sortedJobs = computed(() => {
      const sortTypeValue = sortType.value
      return [...jobs.value].sort((a: Job, b: Job) => {
        return a[sortTypeValue] > b[sortTypeValue] ? 1 : -1
      })
    })

    function handleSortBy(newSortType: SortingTerm) {
      sortType.value = newSortType
    }


    return {sortedJobs, sortType, handleSortBy}
  }
});
</script>

<style>
  #app {
    max-width: 1160px;
    margin-left: auto;
    margin-right: auto;
  }
</style>
