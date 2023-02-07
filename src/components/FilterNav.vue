<template>
  <nav class="filter-nav">
    <button @click="filterBy('all')" :class="{ active : current==='all'}">all</button>
    <button @click="filterBy('complete')" :class="{ active : current==='complete'}">complete</button>
    <button @click="filterBy('ongoing')" :class="{ active : current==='ongoing'}">ongoing</button>
  </nav>
</template>

<script>
export default {
    props:["current"],
    methods:{
        filterBy(value){
            this.$emit("filterValue",value);
        }
    }
}
</script>

<style>
    .filter-nav button{
        border: none;
        outline: none;
        text-transform: uppercase;
        color: #bbb;
        font-weight: bold;
        display: inline-block;
        background: none;
        font-size: .8rem;
        letter-spacing: 2px;
    }
    button.active{
        color: #000;
    }  
</style>