<template>
  <div class="projects-table-view">

    <table border="0" cellspacing="0" cellpadding="0">
      <thead>
        <tr>
          <th>Name</th>
          <th>Process</th>
          <th>Team</th>
          <th>Total Budget</th>
          <th class="event-icon"></th>
        </tr>
      </thead>
      <tbody>

        <ProjectsTableViewItem
          v-for="(item, index) in project"
          :key="index"
          :project="project"
          :item="item"
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


<style lang="scss" scoped>

  .projects-table-view {
    padding: 20px;
    table {
      // padding: 10px;
      width: 100%;
      // border: 1px solid red;
      background-color: white;
      // border-radius: 14px;
      thead {
        tr {
          height: 45px;
          th {
            text-align: left;
            border: solid 1px blue;
          }
        }
      }
    }
  }

</style>
