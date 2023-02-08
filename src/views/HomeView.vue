<template>
  <div class="home">
    <h2>Home</h2>
    <FilterNav @filterValue="current=$event" :current="current"></FilterNav>
    <div v-for="project in filteredProjects" :key="project.id">
      <SingleProject :project="project" @delete="deleteProject" @complete="completeProject"></SingleProject>
    </div>
    {{current}}
  </div>
</template>

<script>
import FilterNav from '../components/FilterNav'
import SingleProject from '../components/SingleProject'
export default {
  name: 'HomeView',
  components: {
    FilterNav,
    SingleProject,
  },
  data(){
    return {
      projects:[],
      current: "all"
    }
  },
  methods:{
    deleteProject(id){
      this.projects=this.projects.filter(project => project.id!=id)
    },
    completeProject(id){
      let findProject = this.projects.find(project => project.id===id);
      findProject.complete=!findProject.complete
    }
  },
  computed:{
    filteredProjects(){
      if(this.current==='complete'){
        return this.projects.filter(project => project.complete)
      }
      if(this.current==='ongoing'){
        return this.projects.filter(project => !project.complete)
      }
      return this.projects;
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
