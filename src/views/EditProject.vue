<template>
  <h1>Edit Project</h1>
  <form @submit.prevent="addProject">
    <label>Project Title</label>
    <input type="text" v-model="title"/>
    <label>Project Detail</label>
    <input type="text" v-model="detail">
    <button @click="UpdateProject" class="updateProject">Update Project</button>
  </form>
</template>

<script>
export default {
    props:['id'],
    data(){
      return{
        title:"",
        detail:""
      }
    },
    mounted(){
      fetch('http://localhost:3000/projects/'+this.id)
      .then((res)=>{
        return res.json();
      })
      .then((datas)=>{
        this.title=datas.title,
        this.detail=datas.detail
      })
      .catch((err)=>{
        console.log(err);
      })
    },
    methods:{
      UpdateProject(){
        fetch('http://localhost:3000/projects/'+this.id,{
          method:"PATCH",
          headers:{
            "Content-Type":"application/json",
          },
          body:JSON.stringify(
            {
              title:this.title,
              detail:this.detail
            }
          )
        })
        .then(()=>{
          this.$router.push('/')
        })
        .catch((err)=>{
          console.log(err)
        })
      }
    }
}
</script>

<style>
  .updateProject{
        display: block;
        background-color: rgb(17, 232, 139);
        border: none;
        padding: 5px;
        border-radius: 7px;
        margin: 0 auto;
  }
</style>