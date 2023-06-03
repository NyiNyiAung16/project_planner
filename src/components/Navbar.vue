<template>
    <nav class="main-nav">
        <router-link to="/">Projects</router-link>
        <router-link :to="{name:'addproject'}">Add Project</router-link>
  </nav>
</template>

<script>
export default {

}
</script>

<style>
    .main-nav{
        text-align: center;
        margin: 40px auto ;
        color: aqua;
    }
    .main-nav a{
        color: rgb(179, 181, 182);
        display: inline-block;
        padding: 10px;
        font-size: 18px;
        text-decoration: none;
    }
    a.router-link-active{
       border-bottom: 3px solid #00ce89;
       padding-bottom: 4px;
    }
</style>