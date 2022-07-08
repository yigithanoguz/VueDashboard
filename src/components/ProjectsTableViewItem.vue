<template>
  <tr class="projects-table-view-item">
    <td>
      <img src="" alt="">
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
    }
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
