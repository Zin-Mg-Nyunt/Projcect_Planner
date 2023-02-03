<template>
  <nav class="nav-bar">
    <router-link to="/">Project</router-link>
    <router-link :to="{name:'AddProject'}">Add Project</router-link>
  </nav>
</template>

<script>
export default {

}
</script>

<style>
    .nav-bar{
        text-align: center;
        margin: 40px 0;
    }
    .nav-bar a{
        text-decoration: none;
        display: inline-block;
        padding: 10px;
        color: #c4c4c4;
        text-transform: uppercase;
        font-weight: 600;
    }
    a.router-link-active{
        border-bottom: 2px solid #00ffaa;
    }
</style>