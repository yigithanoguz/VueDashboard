<template>
  <div class="projects-table-view">
    <ProjectsTopBar />
    <ProjectsTabs />

    <div class="table">
      <table border="0" cellspacing="0" cellpadding="0">
        <thead>
          <tr>
            <th>Name</th>
            <th>Process</th>
            <th>Team</th>
            <th>Total Budget</th>
            <th class="event-icon">Buttons</th>
          </tr>
        </thead>

        <tbody>
          <tr
            class="projects-table-view-item"
            v-for="item in projectList"
            :key="item"
          >
            <td class="name">
              <div>
                <img :src="item.img" alt="logo" />
                {{ item.name }}
              </div>
            </td>
            <td>
              <span class="process" @click="changeProcess(item)">
                <span
                  class="process-color"
                  :class="{
                    'color-orange': item.process == 'In progress',
                    'color-green': item.process == 'Done',
                    'color-gray': item.process == 'Not started',
                  }"
                  >●
                </span>
                <span class="process-name"> {{ item.process }} </span>
              </span>
            </td>
            <td>Team</td>
            <td>
              <div class="budget">
                <span> {{ item.totalBudget * 9999 }} </span>
                <span v-if="item.currency == 'usd'">$</span>
                <span v-else-if="item.currency == 'euro'">€</span>
                <span v-else-if="item.currency == 'sterlin'">£</span>
                <span v-else-if="item.currency == 'tl'">₺</span>
                <span v-else> {{ item.currency }} </span>
              </div>
            </td>
            <td class="event-icon">
              <span class="btn"> View </span>
              <span class="btn" @click="deleteProject(item.id)">
                <i class="bi bi-trash"></i>
              </span>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import ProjectsTopBar from "./ProjectsTopBar.vue";
import ProjectsTabs from "./ProjectsTabs.vue";

export default {
  name: "projects-table-view",
  components: {
    ProjectsTopBar,
    ProjectsTabs,
  },
  props: {
    project: {
      type: Array,
    },
  },
  data() {
    return {
      projectList: [],
      editProcess: '',
    };
  },
  created() {
    axios
      .get("https://6293500f089f87a57abdf537.mockapi.io/project")
      .then((response) => {
        let data = response.data;
        for (let key in data) {
          this.projectList.push({ ...data[key], id: key });
        }
      });
  },
  methods: {
    deleteProject(value) {
      value = Number(value);
      console.log(typeof(value));
      // value += 1;
      axios
        .delete(
          `https://6293500f089f87a57abdf537.mockapi.io/project/${value + 1}`
        )
        .then((response) => {
          console.log(response);
        })
        .catch((e) => console.log(e));

      this.projectList.splice(value, 1);

    },

    changeProcess(value) {

      value.id = Number(value.id);

      console.log(value);
      if (value.process == 'Not started') {
        this.editProcess = 'In progress';

      }
      else if (value.process == 'In progress') {
        this.editProcess = 'Done';
      }

      else {
        this.editProcess = 'Not started';
      }

      console.log(this.editProcess);

      axios.put(`https://6293500f089f87a57abdf537.mockapi.io/project/${value.id + 1}`, { process: this.editProcess })
        .then(response => {
          console.log(response)
        })
        .catch(e => console.log(e));
    }
  },
};
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

.table {
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
        background-color: rgb(247, 236, 255);
        th:nth-child(2n) {
          background-color: rgb(236, 214, 253);
        }


        th {
          padding: 5px;
          &:nth-child(1) {
            padding-left: 10px;
          }
          &:nth-last-child(1) {
            padding-right: 10px;
          }

          text-align: left;
          // border: solid 1px blue;
        }
      }
    }
    tbody {
      tr {
        height: 50px;
        font-size: 0.9rem;
        &:nth-child(2n) {
          background-color: rgb(247, 236, 255);
          td:nth-child(2n) {
            background-color: rgb(236, 214, 253);
          }
        }

        &:nth-child(2n-1) {
          background-color: rgb(255, 255, 255);
          td:nth-child(2n) {
            background-color: rgb(252, 239, 254);
          }
        }

        td {
          // height: 100%;
          padding: 5px;

          &.name {
            font-weight: bold;
          }

          &:nth-child(1) {
            padding-left: 10px;
            > div {
              display: flex;
              align-items: center;
              gap: 10px;
            }
            img {
              height: 40px;
              width: 40px;
            }
          }



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
              box-shadow: rgba(60, 64, 67, 0.3) 0px 1px 2px 0px,
                rgba(60, 64, 67, 0.15) 0px 1px 3px 1px;
              transition: 300ms;
              &:hover {
                box-shadow: rgba(60, 64, 67, 0.3) 0px 1px 2px 0px,
                  rgba(60, 64, 67, 0.15) 0px 2px 6px 2px;
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
