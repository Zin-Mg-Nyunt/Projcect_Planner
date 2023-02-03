<template>
  <h1>Add Project</h1>
  <form @submit.prevent="addProject">
    <label>Project Title</label>
    <input type="text" v-model="title">
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
  methods: {
    addProject(){
      fetch("http://localhost:3000/projects",{
        method:"POST",
        headers:{
          "Content-Type": "application/json"
        },
        body:JSON.stringify({
          title: this.title,
          detail: this.detail,
          complete: false
        })
      })
      .then(()=> this.$router.push("/"))
      .catch(err => err.message())
    }
  }
}
</script>

<style>
  h1{
    text-align: center;
  }
  form{
    min-width: 500px;
    margin-top: 4rem;
  }
  label{
    display: block;
    text-transform: uppercase;
    font-weight: bold;
    letter-spacing: .08rem;
    color: #949494;
    margin-bottom: .5rem;
  }
  input{
    border: none;
    padding: .5rem 0;
    border-bottom: 1px solid #c4c4c4;
    width: 100%;
    margin-bottom: 1.5rem;
    font-size: 1.5rem;
  }
  button{
    display: block;
    margin: 0 auto;
    border-radius: 10px;
    padding: 15px;
    background-color: #00ffaa;
    color: #f0f0f0;
    border: none;
    font-size: 1.1rem;
    font-weight: 600;
    cursor: pointer;
  }
</style>