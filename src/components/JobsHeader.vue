<template lang="">
    <div class="title">
        <h1>JOB BOARD</h1> 
    </div>
    <div class="sort-menu">
        <p class="sort-menu__title">SET SORTING</p>
        <div class="sort-menu__btns">
            <button @click="handleClick('title')">BY TITLE</button>
            <button @click="handleClick('salary')">BY SALARY</button>
        </div>
    </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
import SortingTerm from '@/types/SortingTerm'
export default defineComponent({
    name: 'JobsHeader',
    components: {},
    emits: ['sortBy'],
    setup(props, {emit}) {

        function handleClick(term: SortingTerm) {
            emit('sortBy', term)
        }

        return {handleClick}
    },
})
</script>
<style>
    .title {
        margin-bottom: 20px;
    }
    .title h1{
        text-align: center;
        margin: 0;
        padding: 0;
    }
    .sort-menu{
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
    }
    .sort-menu__btns{
        display: flex;
        gap: 30px;
    }
</style>