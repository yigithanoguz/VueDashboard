<template>
  <div class="home">
    <ProjectsGridView />
  </div>
</template>

<script>
// @ is an alias to /src
import ProjectsGridView from '../components/ProjectsGridView.vue';

export default {
  name: 'Home',
  components: {
    ProjectsGridView,
  }
}
</script>
