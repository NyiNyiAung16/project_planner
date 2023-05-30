<template>
    <div class="main" @click="showDetail=!showDetail">
        <h2>{{project.title}}</h2>
        <p v-if="showDetail">{{project.detail}}</p>
    </div>
</template>

<script>
export default {
    props:['project'],
    data(){
        return{
            showDetail:false
        }
    }
}
</script>

<style>
    .main{
        background-color: rgb(203, 197, 197);
        padding: 20px;
        margin-bottom: 10px;
        border-radius: 4px;
    }
    h2{
        color: indigo;
    }
</style>