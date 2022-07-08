<template>
  <div class="profile">
      <img src="../assets/yigithan.jpg" alt="...">
      <span>Yiğithan Oğuz</span>
      <i class="bi bi-caret-down-fill"></i>
    </div>
</template>


<style lang="scss" scoped>
  $color-purple: rgb(117, 77, 209);

  .profile {
      display: flex;
      align-items: center;
      gap: 10px;
      font-weight: bold;
      font-size: 0.9rem;
      cursor: pointer;
      user-select: none;
      img {
        height: 35px;
        width: 35px;
        border: solid 2px $color-purple;
        border-radius: 50%;
      }
    }
</style>
