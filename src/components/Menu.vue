<template>
  <div class="menu">
    <Logo />
    <MenuItem
      v-for="(item, index) in menuTree"
      :key="index"
      :label="item.label"
      :icon="item.icon"
      :depth="0"
      :data="item.children"
    />
  </div>
</template>

<script>
import Logo from './Logo.vue'
import MenuItem from './MenuItem.vue';

export default {
  name: "menu",
  data: () => ({
    menuTree: [
        {
          label: 'Project',
          icon: 'bi-briefcase-fill',
          children: [
            {
              label: 'Grid View',
              to: '/about',
            },
            {
              label: 'Table View',
            },
            {
              label: 'Details',
            },
            {
              label: 'Create a new project',
            }
          ]
        },
        {
          label: 'Tasks',
          icon: 'bi-list-task',
          children: [
            {
              label: 'List View',
            },
            {
              label: 'Board View',
            },
            {
              label: 'Create task',
            }
          ]
        },
        {
          label: 'User',
          icon: 'bi-people-fill',
          children: [
            {
              label: 'Profile',
            },
            {
              label: 'Table View',
            },
            {
              label: 'Permissions',
            }
          ]
        },
        {
          label: 'Settings',
          icon: 'bi-gear-fill',
          children: [
            {
              label: 'General',
            },
            {
              label: 'Security',
            }
          ]
        },
        {
          label: 'Authentication',
          icon: 'bi-person-bounding-box',
          children: [
            {
              label: 'Login',
              to: 'login'
            },
            {
              label: 'Register',
            }
          ]
        }
      ]
  }),
  components: {
    Logo,
    MenuItem
  }
}
</script>

<style lang="scss" scoped>
  // $color-purple: rgb(117, 77, 209);

  .menu {
    height: 100vh;
    width: 280px;
    // border-right: 1px solid blue;
    background-color: rgb(255, 249, 255);
    overflow: auto;
    transition: all 300ms ease;
    box-sizing: border-box;
    position: fixed;
    top: 0;
    left: 0;
    box-shadow: rgba(60, 64, 67, 0.3) 0px 1px 2px 0px, rgba(60, 64, 67, 0.15) 0px 1px 3px 1px;
  }
  /* width */
::-webkit-scrollbar {
  width: 5px;
}

/* Track */
::-webkit-scrollbar-track {
  box-shadow: inset 0 0 5px rgb(195, 195, 195);
  border-radius: 10px;
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: gray;
  border-radius: 10px;
}
</style>
