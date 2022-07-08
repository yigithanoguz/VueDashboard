<template>
  <div class="projects-tab-group">
    <span class="tab">Grid View</span>
    <span class="tab">Table View</span>
    <span class="tab">Details View</span>
    <span class="tab">Create Project</span>
  </div>
</template>

<script>
export default {
  name: 'projects-tab-group',

}
</script>

<style lang="scss" scoped>
.projects-tab-group {
  height: 45px;
  padding-top: 20px;
  margin: 0 20px;
  display: flex;
  gap: 30px;
  border-bottom: gray solid 1px;
  .tab {
    height: 100%;
    padding-bottom: 10px;
    cursor: pointer;
    font-size: 0.9rem;
    &:hover {
      border-bottom: 1px gray solid;
    }
  }
}
</style>
