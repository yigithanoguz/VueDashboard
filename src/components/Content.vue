<template>
  <div class="content">
    <Header />
    <router-view></router-view>
    <!-- <ProjectsGridView /> -->

    <!-- <ProjectsTableView :project="project" />
    <CreateProject /> -->
  </div>
</template>

<script>

import Header from './Header.vue';
// import ProjectsGridView from './ProjectsGridView.vue';
// import ProjectsTableView from './ProjectsTableView.vue';
// import CreateProject from './CreateProject.vue';

export default {
  name: 'App',
  components: {
    Header,
    // ProjectsGridView,
    // ProjectsTableView,
    // CreateProject
  },
  props: {
    project: {
      type: Array
    }
  },
  data() {
    return {
      user: {

      }
    }
  }
}
</script>

<style lang="scss" scoped>
  .content {
    width: 100%;
  }
</style>


