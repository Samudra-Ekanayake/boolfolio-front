<script>
import axios from "axios";

/*  import HelloWorld from './components/HelloWorld.vue'*/

export default {
  name: 'App',
  data() {
    return {
      url: 'http://127.0.0.1:8000',
      projects: null
    }
  },
  mounted() {
    axios
      .get(`${this.url}/api/projects`)
      .then(response => {
        console.log(response);
        this.projects = response.data;
      })
      .catch(error => {
        console.error("Errore durante il recupero dei progetti:", error);
      });
  },
}
</script>

<template>

  <div class="container p-3">
    <h1 class="py-5">Projects</h1>
    <div class="row row-cols-1 g-3">
      <div class="row" v-if="projects && projects.project && projects.project.data">
        <div class="col-4 g-1" v-for="progetto in projects.project.data">
          <div class="card h-100">
            <img class="card-img-top img-fluid" :src="progetto.cover_image" alt="">
            <div class="card-body">
              <h5 class="card-title">{{ progetto.name }}</h5>
              <p class="card-text">{{ progetto.description }}</p>
              <a href="#" class="btn btn-primary">Go somewhere</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
