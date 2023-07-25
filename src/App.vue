<script>
import axios from 'axios';
import AppHeader from './components/AppHeader.vue';
import AppFooter from './components/AppFooter.vue';

export default{
  components: {
        AppFooter,
        AppHeader,
    },

  data(){
      return{
        projects:[],
        currentPage:'',
      }
  },
  methods: {
    getallresult(){
      axios.get("http://localhost:8000/api/projects", {})
      .then(rensponse => this.projects = rensponse.data.data);
    } 
  },
  created() {
    this.getallresult();

  },

}

</script>


 
<template>
  <AppHeader />

  <div
  class="card" 
  v-for="project in projects" 
  :key="project.id">
    <h2>
      {{project.name}}
    </h2>
    <h3>{{ project.category.name }}</h3>
  </div>

  <AppFooter />
</template>




<style lang="scss">


</style>