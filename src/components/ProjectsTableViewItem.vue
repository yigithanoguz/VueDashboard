<template>
  <tr class="projects-table-view-item">
    <td>
      <!-- <img src="" alt=""> -->
      {{ name }}
    </td>
    <td>
      <span class="process" @click="changeProcess">
        <span class="process-color" :class="{ 'color-orange': process=='In progress', 'color-green': process=='Done', 'color-gray': process=='Not started' }">● </span>
        <span class="process-name"> {{ process }} </span>
      </span>
    </td>
    <td>
      Team
    </td>
    <td>
      <div class="budget">
        <span v-if="currency=='USD'">$</span>
        <span v-else> {{ currency }} </span>
        <span> {{ totalBudget }} </span>
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
</template>

<script>

export default {
  name: 'projects-table-view-item',
  data: () => ({
    processColor: null
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
    },
    deleteProject(value) {
      console.log(this.item);
      this.project.pop(value);
    }
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
</style>
