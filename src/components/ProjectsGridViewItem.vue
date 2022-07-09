<template>
  <!-- <div class="card">
    <div class="card-header">
      <div class="process">
        <span class="process-color">● </span>
        <span class="process-name">In progress</span>
      </div>
      <div class="icons">
        <i class="bi bi-arrow-clockwise"></i>
        <i class="bi bi-three-dots"></i>
      </div>
    </div>

    <div class="card-body">
      <div class="card-img">
        <img src="../assets/logo.png" alt="logo" />
      </div>
      <div class="card-title">Website Redesign</div>
      <div class="card-icons">
        <i class="bi bi-bar-chart-fill"></i>
        <i class="bi bi-bar-chart-fill"></i>
        <i class="bi bi-bar-chart-fill"></i>
      </div>
      <div class="card-details">Details</div>
    </div>
  </div> -->


  <!-- <div class="card">
    <div class="card-header">
      <div class="process">
        <span class="process-color" :class="{ 'color-orange': process=='In progress', 'color-green': process=='Done', 'color-gray': process=='Not started' }">● </span>
        <span class="process-name"> {{ process }} </span>
      </div>
      <div class="icons">
        <i class="bi bi-arrow-clockwise" @click="changeProcess()"></i>
        <i class="bi bi-three-dots"></i>
      </div>
    </div>

    <div class="card-body">
      <div class="card-img">
        <img :src="img" alt="logo" />
      </div>
      <div class="card-title"> {{ name }} </div>
      <div class="card-icons">
        <i class="bi bi-bar-chart-fill"></i>
        <i class="bi bi-bar-chart-fill"></i>
        <i class="bi bi-bar-chart-fill"></i>
      </div>
      <div class="card-details">
        <div class="budget">
          <span v-if="currency=='USD'">$</span>
          <span v-else> {{ currency }} </span>
          <span> {{ totalBudget }} </span>
        </div>
        <div class="info">
          Total Budget
        </div>
      </div>
    </div>
  </div> -->

  <div class="card">
    <div class="card-header">
      <div class="process">
        <span class="process-color" :class="{ 'color-orange': process=='In progress', 'color-green': process=='Done', 'color-gray': process=='Not started' }">● </span>
        <span class="process-name"> {{ process }} </span>
      </div>
      <div class="icons">
        <i class="bi bi-arrow-clockwise" @click="changeProcess()"></i>
        <i class="bi bi-three-dots"></i>
      </div>
    </div>

    <div class="card-body">
      <div class="card-img">
        <img :src="img" alt="logo" />
      </div>
      <div class="card-title"> {{ name }} </div>
      <div class="card-icons">
        <i class="bi bi-bar-chart-fill"></i>
        <i class="bi bi-bar-chart-fill"></i>
        <i class="bi bi-bar-chart-fill"></i>
      </div>
      <div class="card-details">
        <div class="budget">
          <span v-if="currency=='USD'">$</span>
          <span v-else> {{ currency }} </span>
          <span> {{ totalBudget }} </span>
        </div>
        <div class="info">
          Total Budget
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'projects-grid-view-item',
  data: () => ({
    // processColor: null
  }),
  props: {
    name: {
      type: String,
      // required: true,
    },
    img: {
      type: String,
      // required: true,
    },
    process: {
      type: String,
      // required: true,
    },
    totalBudget: {
      type: Number,
    },
    currency: {
      type: String,
    },
    item: {
      type: Object,
    },
    project: {
      type: Array,
    },
  },
  methods: {
    changeProcess() {
      if (this.process == 'Not started') {
        this.process = 'In progress';

      }
      else if (this.process == 'In progress')
        this.process = 'Done';

      else this.process = 'Not started';
    }
  }
}
</script>

<style lang="scss" scoped>

$color-white: white;

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
</style>
