<template>
  <div class="sidebar-container" id="sidebar">
    <div>

    </div>
    <!-- <ul class="navbar-nav">
      <li class="nav-item">
        <a class="nav-link" href="#">Project</a>

          <ul class="nav">
            <li class="nav-item">
              <a class="nav-link" href="#">Grid View</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Table View</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Details</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Create Projects</a>
            </li>
          </ul>

      </li>

      <li class="nav-item">
        <a class="nav-link" href="#">Tasks</a>

          <ul class="nav">
            <li class="nav-item">
              <a class="nav-link" href="#">List View</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Board View</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Create Task</a>
            </li>
          </ul>

      </li>

      <li class="nav-item">
        <a class="nav-link" href="#">Users</a>

          <ul class="nav">
            <li class="nav-item">
              <a class="nav-link" href="#">Profile</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Table View</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Permissions</a>
            </li>
          </ul>

      </li>

      <li class="nav-item">
        <a class="nav-link" href="#">Settings</a>

          <ul class="nav">
            <li class="nav-item">
              <a class="nav-link" href="#">General</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Security</a>
            </li>
          </ul>

      </li>

      <li class="nav-item">
        <a class="nav-link" href="#">Authentication</a>

          <ul class="nav">
            <li class="nav-item">
              <a class="nav-link" href="#">Login</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Register</a>
            </li>
          </ul>

      </li>
    </ul> -->
  </div>
</template>

<script>
export default {
  name: "Sidebar",
  data: () => {
    return {
      menuTree: [
        {
          label: 'Project',
          children: [
            {
              label: 'Grid View',
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
          label: 'Users',
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
          children: [
            {
              label: 'Login',
            },
            {
              label: 'Register',
            }
          ]
        }
      ]
    }
  },
  methods: {
    test: false,
  }
}

</script>

<style scoped lang="scss">
@import "bootstrap";

  .nav {
    display: none;
  }

  .nav.active {
    display: block;
  }


</style>
