<template>
    <nav class="main-nav">
        <router-link :to="{name:'Home'}">Projects</router-link>
        <router-link :to="{name:'AddProject'}">Add a new project</router-link>
    </nav>
</template>

<script>
export default {

}
</script>

<style>
    .main-nav{
        text-align: center;
        margin: 40px auto;
    }
    .main-nav a{
        text-decoration: none;
        display:inline-block;
        margin: 0 10px;
        color: #999;
        font-size:20px;
    }
    a.router-link-active{
        border-bottom:4px solid #00ce89;
        border-radius: 5px;
        padding-bottom: 4px;
    }
</style>