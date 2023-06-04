<template>
  <nav class="filter-nav">
    <button @click="filterby('all')" :class="{ active : current==='all'}">all</button>
    <button @click="filterby('complete')" :class="{ active : current==='complete'}">complete</button>
    <button @click="filterby('ongoing')" :class="{ active : current==='ongoing'}">ongoing</button>
  </nav>
</template>

<script>
export default {
    props:['current'],
    methods:{
        filterby(value){
            this.$emit('filtervalue',value)
        }
    }
}
</script>

<style>
    .filter-nav button {
        color: rgb(181, 180, 179);
        margin-left: 4px;
        text-transform: uppercase;
        border: none;
        background-color: white;
        margin-bottom: 6px;
        cursor: pointer;
    }
    button.active{
        color: rgb(45, 43, 43);
    }
</style>