<script>
import axios from "axios";

/*  import HelloWorld from './components/HelloWorld.vue'*/

export default {
  name: 'App',
  data() {
    return {
      url: 'http://127.0.0.1:8000',
      projects: ''
    }
  },
  mounted() {
    axios
      .get(`${this.url}/api/projects`)
      .then(response => {
        console.log(response);
        this.projects = response.data.projects
      })
  },
}
</script>

<template>

</template>

<style scoped></style>
