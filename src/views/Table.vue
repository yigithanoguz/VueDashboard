<template>
  <div class="table">
    <ProjectsTableView />
  </div>
</template>

<script>
// @ is an alias to /src
import ProjectsTableView from '../components/ProjectsTableView.vue';

export default {
  name: 'Home',
  components: {
    ProjectsTableView,
  }
}
</script>
