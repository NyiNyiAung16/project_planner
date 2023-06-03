<template>
  <h1>Add Project</h1>
  <form @submit.prevent="addProject">
    <label>Project Title</label>
    <input type="text" v-model="title"/>
    <label>Project Detail</label>
    <input type="text" v-model="detail">
    <button>Add Project</button>
  </form>
</template>

<script>
export default {
    data(){
        return{
            title:"",
            detail:""
        }
    },
    methods:{
        addProject(){
            fetch("http://localhost:3000/projects",{
                method:"POST",
                headers:{"Content-Type":"application/json"},
                body:JSON.stringify(
                    {
                        title:this.title,
                        detail:this.detail,
                        complete:false
                    }
                )
            })
            .then(()=>{
                this.$router.push('/')
            })
            .catch((err)=>{
                console.log(err);
            })
        }
    }
}
</script>

<style>
    form{
        background-color: rgb(220, 216, 212);
        padding: 30px;
        border-radius: 10px;
        max-width: 420px;
    }
    label{
        color: rgb(168, 167, 166);
        margin-bottom: 20px;
        text-transform: uppercase;
        display: block;
        font-size: 15px;
        letter-spacing: 1px;
    }
    input{
        border: none;
        padding: 10px;
        border-bottom: 1px solid rgb(180, 176, 176);
        margin-bottom: 20px;
        border-radius: 2px;
        width: 100%;
        background-color:  rgb(220, 216, 212);
    }
    button{
        display: block;
        background-color: rgb(17, 232, 139);
        border: none;
        padding: 5px;
        border-radius: 7px;
        margin: 0 auto;
    }
</style>