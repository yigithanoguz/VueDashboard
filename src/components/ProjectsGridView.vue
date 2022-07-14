<template>
  <div class="projects-grid-view">

    <ProjectsTopBar />
    <ProjectsTabs />

    <div class="grid">
      <div class="card" v-for="post in projectList" :key="post">
        <div class="card-header">
          <div class="process">
            <span class="process-color" :class="{ 'color-orange': post.process=='In progress', 'color-green': post.process=='Done', 'color-gray': post.process=='Not started' }">● </span>
            <span class="process-name"> {{ post.process }} </span>
          </div>
          <div class="icons">
            <i class="bi bi-arrow-clockwise" @click="changeProcess(post)"></i>
            <i class="bi bi-three-dots"></i>
          </div>
        </div>

        <div class="card-body">
          <div class="card-img">
            <img :src="post.img" alt="logo" />
          </div>
          <div class="card-title"> {{ post.name }} </div>
          <div class="card-icons">
            <i class="bi bi-bar-chart-fill"></i>
            <i class="bi bi-bar-chart-fill"></i>
            <i class="bi bi-bar-chart-fill"></i>
          </div>
          <div class="card-details">
            <div class="budget">
              <span> {{ post.totalBudget * 9999 }} </span>
              <span v-if="post.currency=='usd'">$</span>
              <span v-else-if="post.currency=='euro'">€</span>
              <span v-else-if="post.currency=='sterlin'">£</span>
              <span v-else-if="post.currency=='tl'">₺</span>
              <span v-else> {{ post.currency }} </span>
            </div>
            <div class="info">
              Total Budget
            </div>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
import axios from "axios";
import ProjectsTopBar from './ProjectsTopBar.vue';
import ProjectsTabs from './ProjectsTabs.vue';

export default {
  name: 'project-grid-view',
  components: {
    ProjectsTopBar,
    ProjectsTabs
  },
  props: {
    project: {
      type: Array
    }
  },
  data() {
    return {
      projectList: [],
      editProcess: '',
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
  },
  methods: {
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
  }
}
</script>

<style lang="scss" scoped>
$color-white: white;

  .projects-grid-view {

    .grid {
      padding: 20px;
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 20px;

      .card {
        // height: 400px;
        padding: 25px;

        background-color: $color-white;
        border-radius: 20px;
        transition: all 400ms ease;

        box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 6px -1px, rgba(0, 0, 0, 0.06) 0px 2px 4px -1px;
        &:hover {
          box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
        }

        i {
          cursor: pointer;
          transition: all 300ms ease;
          color: gray;
          &:hover {
            color: purple;
          }
        }

        .card-header {
          display: flex;
          justify-content: space-between;

          .process {


            // .process-color {
            //   color: orange;
            // }
            .color-orange {
              color: orange;
            }
            .color-gray {
              color: gray;
            }
            .color-green {
              color: rgb(6, 225, 6);
            }

            .process-name {
              font-size: 0.9rem;
              font-weight: bold;
            }

          }

          .icons {
            display: flex;
            gap: 10px;
            font-size: 1.1rem;
          }
        }

        .card-body {
          margin-top: 50px;
          height: 100%;
          display: flex;
          flex-direction: column;
          align-items: center;
          .card-img {
            img {
              height: 50px;
              width: 50px;
            }
          }
          .card-title {
            margin-top: 30px;
            font-weight: bold;
            cursor: pointer;
            transition: all 300ms ease;
            &:hover {
              color: purple;
            }
          }
          .card-icons {
            width: 100%;
            margin-top: 30px;
            display: flex;
            justify-content: space-around;
          }
          .card-details {
            width: 100%;
            margin-top: 20px;
            padding-top: 20px;
            border-top: solid 1px gray;
            text-align: center;
            .budget {
              font-weight: bold;
            }
            .info {
              margin-top: 10px;
              font-size: 0.9rem;
              color: gray;
            }
          }
        }
      }
    }


  }
</style>
