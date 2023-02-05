<template>
        <div class="project" :class="{complete:this.project.complete}">
            <div class="flexing">
                <div>
                    <h3 @click="showDetail=!showDetail">{{project.title}}</h3>
                </div>
                <div class="icon-div">
                    <i class="fa-solid fa-trash" @click="deleteProject"></i>
                    <router-link :to="{name:'EditProject',params:{id:this.project.id}}">
                        <i class="fa-solid fa-pen"></i>
                    </router-link>
                    <i class="fa-solid fa-check" @click="completeProject"></i>
                </div>
            </div>
            <p v-if="showDetail">{{project.detail}}</p>
        </div>
</template>

<script>
export default {
    props:['project'],
    data(){
        return{
            showDetail:false,
            api: "http://localhost:3000/projects/"
        }
    },
    methods:{
        deleteProject(){
            let deleteProjectApi = this.api+this.project.id;
            fetch(deleteProjectApi, {method:"DELETE"})
            .then(this.$emit('delete',this.project.id))
            .catch(err=> console.log(err.message()))
        },
        completeProject(){
            let updateCompleteProjectApi = this.api+this.project.id;
            fetch(updateCompleteProjectApi,{
                method: "PATCH",
                headers:{
                    "Content-Type": "application/json",
                },
                body:JSON.stringify({
                    complete:!this.project.complete
                })
            })
            .then(this.$emit('complete',this.project.id))
            .catch(err=> console.log(err.message()))
        }
    }
}
</script>

<style>
    .project{
        padding: 20px;
        background-color: #f2f2f2;
        margin: 10px 0;
        border-radius: .4rem;
        border-left: solid 5px crimson;
    }
    .complete{
        border-left-color: green;
    }
    h3{
        cursor: pointer;
        color: indigo;
    }
    .flexing{
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    .icon-div i{
        cursor: pointer;
        padding-left: 10px;
    }
    .icon-div i:hover{
        color: #9999;
    }
</style>