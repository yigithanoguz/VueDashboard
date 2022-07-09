<template>
  <div class="content">
    <ProjectsGridView :project="project" />
    <!-- <ProjectsTableView :project="project" />
    <CreateProject /> -->
  </div>
</template>

<script>

import ProjectsGridView from './ProjectsGridView.vue';
// import ProjectsTableView from './ProjectsTableView.vue';
// import CreateProject from './CreateProject.vue';

export default {
  name: 'App',
  components: {
    ProjectsGridView,
    // ProjectsTableView,
    // CreateProject
  },
  props: {
    project: {
      type: Array
    }
  }
}
</script>

<style lang="scss" scoped>
  .content {
    width: 100%;
  }
</style>


