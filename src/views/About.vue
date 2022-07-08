<template>
  <div class="about">
    <Sidebar />
  </div>
</template>

<script>
import Sidebar from '@/components/Sidebar.vue'

export default {
  name: 'About',
  components: {
    Sidebar
  }
}
</script>

<style scoped lang="scss">
  .about {
    display: flex;
  }
</style>
