<template>
  <div class="header">
    <Profile />
  </div>
</template>

<script>
import Profile from './Profile.vue'

export default {
  name: 'header',
  components: {
    Profile
  }
}
</script>

<style lang="scss" scoped>
  .header {
    height: 60px;
    width: 100%;
    padding: 0 20px;
    box-sizing: border-box;
    border-bottom: solid 1px blue;
    display: flex;
    justify-content: flex-end;
    align-items: center;
  }
</style>
