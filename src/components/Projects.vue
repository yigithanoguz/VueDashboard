<template>
  <div class="projects">
    <Header />
    <ProjectsTopBar />
    <ProjectsTabs />
    <ProjectsGridView :project="project" />
    <ProjectsTableView :project="project" />
  </div>
</template>

<script>
import Header from './Header.vue';
import ProjectsTopBar from './ProjectsTopBar.vue';
import ProjectsTabs from "./ProjectsTabs.vue";
import ProjectsGridView from './ProjectsGridView.vue';
import ProjectsTableView from './ProjectsTableView.vue';

export default {
  name: 'App',
  components: {
    Header,
    ProjectsTopBar,
    ProjectsTabs,
    ProjectsGridView,
    ProjectsTableView,
  },
  props: {
    project: {
      type: Array
    }
  }
}
</script>

<style lang="scss" scoped>
  .projects {
    width: 100%;
  }
</style>


