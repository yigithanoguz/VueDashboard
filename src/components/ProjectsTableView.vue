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

        <!-- <ProjectsTableViewItem
          v-for="(item, index) in project"
          :key="index"
          :project="project"
          :item="item"
          :name="item.name"
          :img="item.img"
          :process="item.process"
          :totalBudget="item.totalBudget"
          :currency="item.currency"
        /> -->


        <tr class="projects-table-view-item" v-for="post in projectList" :key="post">
          <td>
            <!-- <img src="" alt=""> -->
            {{ post.name }}
          </td>
          <td>
            <span class="process" @click="changeProcess">
              <span class="process-color" :class="{ 'color-orange': post.process=='In progress', 'color-green': post.process=='Done', 'color-gray': post.process=='Not started' }">● </span>
              <span class="process-name"> {{ post.process }} </span>
            </span>
          </td>
          <td>
            Team
          </td>
          <td>
            <div class="budget">
              <span v-if="post.currency=='USD'">$</span>
              <span v-else> {{ post.currency }} </span>
              <span> {{ post.totalBudget }} </span>
            </div>
          </td>
          <td class="event-icon">
            <span class="btn">
              View
            </span>
            <span class="btn" @click="deleteProject(key)">
              <i class="bi bi-trash"></i>
            </span>
          </td>
        </tr>

      </tbody>
    </table>


  </div>
</template>

<script>
import axios from "axios";

// import ProjectsTableViewItem from './ProjectsTableViewItem.vue';

export default {
  name: 'projects-table-view',
  components: {
    // ProjectsTableViewItem
  },
  props: {
    project: {
      type: Array
    }
  },
  data() {
    return {
      projectList: [],
    }
  },
  created() {
    axios.get('https://6293500f089f87a57abdf537.mockapi.io/project')
      .then(response => {
        let data = response.data;
        for(let key in data) {
          this.projectList.push({ ...data[key], id: key });
        }
      })
  }
}
</script>


<style lang="scss" scoped>

  .color-orange {
    color: orange;
  }
  .color-gray {
    color: gray;
  }
  .color-green {
    color: rgb(6, 225, 6);
  }

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
      tbody {

        tr {
          height: 50px;
          font-size: 0.9rem;
          &:nth-child(2n) {
            background-color: rgb(247, 236, 255);
          }
          td {
            height: 100%;
            &.event-icon {
              // padding-right: 10px;
              text-align: right;
              .btn {
                margin-right: 10px;
                display: inline-block;
                // border: solid 1px gray;
                padding: 5px;
                border-radius: 8px;
                cursor: pointer;
                background-color: white;
                box-shadow: rgba(60, 64, 67, 0.3) 0px 1px 2px 0px, rgba(60, 64, 67, 0.15) 0px 1px 3px 1px;
                transition: 300ms;
                &:hover {
                  box-shadow: rgba(60, 64, 67, 0.3) 0px 1px 2px 0px, rgba(60, 64, 67, 0.15) 0px 2px 6px 2px;
                }
              }
            }
            .process {
              cursor: pointer;
              user-select: none;
            }

          }
        }
      }
    }
  }

</style>
