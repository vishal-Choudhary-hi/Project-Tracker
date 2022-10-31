<template>
  <nav class="filter-nav">
    <button @click="updateFilter('all')" :class="{active:current==='all'}">View All</button>
    <button @click="updateFilter('completed')" :class="{active:current==='completed'}">Completed</button>
    <button @click="updateFilter('ongoing')" :class="{active:current==='ongoing'}">Ongoing</button>
  </nav>
</template>

<script>
export default {
    props:['current'],
    methods: {
        updateFilter(by){
            this.$emit('filter',by)
        }
    }
}
</script>

<style>
    .filter-nav button{
        background:none;
        border:0;
        color:#bbb;
        outline:none;
        font-size: 14px;
        text-transform: uppercase;
        margin-right: 10px;
        letter-spacing: 2px;
        font-weight: bold;
        cursor: pointer;
    }
    .filter-nav .active{
        color:black;
    }
</style>