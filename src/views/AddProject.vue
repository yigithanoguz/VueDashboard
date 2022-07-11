<template>
  <div class="add-project">
    <CreateProject />
  </div>
</template>

<script>
// @ is an alias to /src
import CreateProject from '../components/CreateProject.vue';

export default {
  name: 'Home',
  components: {
    CreateProject,
  }
}
</script>
