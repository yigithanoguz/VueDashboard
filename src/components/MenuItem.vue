<template>
  <router-link tag="div" to="" class="menu-item">
    <a class="label"
      @click="toggleMenu()"
      :style="{
        paddingLeft: depth * 30 + 20 + 'px'
      }"
    >
      <div class="left">
        <i v-if="icon" class="bi" :class="icon"></i>
        <span> {{ label }} </span>
      </div>
      <div v-if="data" class="right">
        <i class="bi bi-caret-down-fill" :class="{ expanded: expanded }"></i>
      </div>
    </a>
    <div
      class="items-container"
      v-show="showChildren"
      ref="container"
      :style="{ height: containerHeight }"
    >



      <menu-item
        v-for="(item, index) in data"
        :key="index"
        :label="item.label"
        :icon= item.icon
        :depth="depth + 1"
        :data="item.children"
        :to="item.link"
      />

      <!-- </router-link> -->


    </div>
  </router-link>
</template>

<script>
export default {
  name: 'menu-item',
  data: () => ({
    showChildren: false,
    expanded: false,
    containerHeight: 0,
  }),
  props: {
    label: {
      type: String,
      required: true,
    },
    icon: {
      type: String,
    },
    depth: {
      type: Number,
      required: true,
    },
    data: {
      type: Array,
    },
    // link: {
    //   type: String,
    // }
  },
  methods: {
    toggleMenu() {
      this.expanded = !this.expanded;
      if(!this.showChildren) {
        this.showChildren = true;
        this.$nextTick(() => {
          this.containerHeight = this.$refs["container"].scrollHeight + "px";
          setTimeout(() => {
            this.containerHeight = "fit-content";
            this.$refs["container"].style.overflow = "visible";
          },300)
        })
      }
      else {
        setTimeout(() => {
          this.containerHeight = 0 + "px";
        },10)
        this.containerHeight = this.$refs["container"].scrollHeight + "px";
        this.$refs["container"].style.overflow = "hidden";
        setTimeout(() => {
          this.showChildren = false;
        },300)
      }
    }
  }
}
</script>

<style lang="scss" scoped>
  $color-purple: rgb(117, 77, 209);
  $color-gray: gray;
  $color-hover: rgb(247, 236, 255);

  .menu-item {
    width: 100%;
    position: relative;
    .label {
      height: 50px;
      display: flex;
      padding: 0 20px;
      justify-content: space-between;
      align-items: center;
      white-space: nowrap;
      user-select: none;
      box-sizing: border-box;
      color: $color-gray;
      font-weight: bold;
      font-size: 0.8rem;
      transition: all 300ms ease;
      cursor: pointer;
      > div {
        display: flex;
        align-items: center;
        gap: 10px;
        transition: all 300ms ease;
      }
      i {
        font-size: 1rem;
        color: $color-gray;
        transition: all 300ms ease;
        &.bi-caret-down-fill {
          font-size: 1rem;
          color: $color-gray;
          &.expanded {
            transform: rotate(-180deg);
          }
        }
      }
      &:hover {
        background-color: $color-hover;
        .left {
          margin-left: 15px;
          color: $color-purple;
        }
      }
    }
    .items-container {
      width: 100%;
      overflow: hidden;
      transition: height 300ms ease;
    }
  }
</style>
