<template>
    <div class="main" :class="{complete:project.complete}">
        <div class="flexing">
            <div>
                <h2  @click="showDetail=!showDetail">{{project.title}}</h2>
            </div>
            <div>
                <span class="material-symbols-outlined icon" @click="deleteProject">
                    delete
                </span>
            <router-link :to="{name:'editproject',params:{id:project.id}}">
                <span class="material-symbols-outlined icon">
                    edit
                </span>
            </router-link>
            <span class="material-symbols-outlined icon" @click="completeProject">
                done
            </span>
            </div>
        </div>
        <p v-if="showDetail">{{project.detail}}</p>
        {{project.complete}}
    </div>
</template>

<script>
export default {
    props:['project'],
    data(){
        return{
            showDetail:false,
            api:'http://localhost:3000/projects/'
        }
    },
    methods:{
        deleteProject(){
            fetch(this.api+this.project.id,{method:'DELETE'})
            .then(()=>{
                this.$emit('delete',this.project.id)
            })
            .catch((err)=>{
                console.log(err)
            })
        },
        completeProject(){
            let apiRoute=this.api+this.project.id;
            fetch(apiRoute,{
                method:"PATCH",
                headers:{
                    "Content-Type":"application/json"
                },
                body:JSON.stringify({
                    complete:!this.project.complete
                })
            })
            .then(()=>{
                this.$emit('complete',this.project.id)
            })
            .catch((err)=>{
                console.log(err)
            })
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
        border-radius: 8px;
        border-left: 6px solid red;
    }
    h2{
        color: indigo;
        cursor: pointer;
    }
    .flexing{
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    span{
        cursor: pointer;
    }
    span:hover{
        color:indigo;
    }
    .icon{
        margin-left: 6px;
    }
    .complete{
        border-left-color: green;
    }
</style>