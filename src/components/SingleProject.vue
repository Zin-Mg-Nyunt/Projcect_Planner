<template>
        <div class="project">
            <div class="flexing">
                <div>
                    <h3 @click="showDetail=!showDetail">{{project.title}}</h3>
                </div>
                <div class="icon-div">
                    <i class="fa-solid fa-trash"></i>
                    <i class="fa-solid fa-pen"></i>
                    <i class="fa-solid fa-check"></i>
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
            showDetail:false
        }
    },
    methods:{
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