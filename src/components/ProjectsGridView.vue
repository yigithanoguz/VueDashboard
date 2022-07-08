<template>
  <div class="projects-grid-view">
    <ProjectsGridViewItem
      v-for="(item, index) in project"
      :key="index"
      :name="item.name"
      :img="item.img"
      :process="item.process"
      :totalBudget="item.totalBudget"
      :currency="item.currency"
    />
  </div>
</template>

<script>
import ProjectsGridViewItem from './ProjectsGridViewItem.vue';

export default {
  name: 'project-grid-view',
  components: {
    ProjectsGridViewItem
  },
  props: {
    project: {
      type: Array
    }
  }
}
</script>

<style lang="scss" scoped>
  .projects-grid-view {
    padding: 20px;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 20px;
  }
</style>
