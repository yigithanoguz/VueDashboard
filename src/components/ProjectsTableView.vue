<template>
  <div class="projects-table-view">

    <table>
      <thead>
        <tr>
          <th>Name</th>
          <th>Process</th>
          <th>Team</th>
          <th>Total Budget</th>
        </tr>
      </thead>
      <tbody>

        <ProjectsTableViewItem
          v-for="(item, index) in project"
          :key="index"
          :name="item.name"
          :img="item.img"
          :process="item.process"
          :totalBudget="item.totalBudget"
          :currency="item.currency"
        />

      </tbody>
    </table>


  </div>
</template>

<script>
import ProjectsTableViewItem from './ProjectsTableViewItem.vue';

export default {
  name: 'projects-table-view',
  components: {
    ProjectsTableViewItem
  },
  props: {
    project: {
      type: Array
    }
  }
}
</script>
