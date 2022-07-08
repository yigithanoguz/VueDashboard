<template>
  <div class="top-bar">
    <div class="title">
      <h2>My Projects</h2>
      <button @mouseover="hover=true" @mouseleave="hover=false">
        <i :class="{ 'bi-plus-square-dotted': !hover, 'bi-plus-square': hover }" class="bi"></i>
        Create
      </button>
    </div>
  </div>
</template>

<script>

export default {
  data: () => ({
    hover: false,
  })
}
</script>

<style lang="scss" scoped>
  $color-purple: rgb(117, 77, 209);

  .top-bar {
    width: 100%;
    height: 60px;
    padding: 0 20px;
    border-bottom: blue solid 1px;
    // display: flex;
    // flex-direction: column;
    .title {
      width: 100%;
      height: 100%;
      display: flex;
      justify-content: space-between;
      align-items: center;
      button {
      height: 45px;
      width: 120px;
      cursor: pointer;
      border-radius: 10px;
      border: none;
      background-color: $color-purple;
      color: white;
      font-size: 1rem;
      font-weight: bold;
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 8px;
      }
    }


  }
</style>
