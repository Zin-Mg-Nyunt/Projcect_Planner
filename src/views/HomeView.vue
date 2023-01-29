<template>
  <div class="home">
    <h2>Home</h2>
    <div v-for="project in projects" :key="project.id">
      <SingleProject :project="project" @delete="deleteProject"></SingleProject>
    </div>
  </div>
</template>

<script>
import SingleProject from '../components/SingleProject'
export default {
  name: 'HomeView',
  components: {
    SingleProject,
  },
  data(){
    return {
      projects:[]
    }
  },
  methods:{
    deleteProject(id){
      this.projects=this.projects.filter(project => project.id!=id)
    }
  },
  mounted(){
    fetch("http://localhost:3000/projects")
    .then(response=> response.json())
    .then(datas=> this.projects=datas)
    .catch(err=> err.message())
  }
}
</script>
