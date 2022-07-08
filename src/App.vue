<template>
  <div id="app">
    <Menu />
    <Projects
      :project="project"
    />
    <!-- <router-view/> -->
  </div>
</template>

<script>
import Menu from './components/Menu.vue'
import Projects from './components/Projects.vue'

export default {
  name: 'App',
  components: {
    Menu,
    Projects,
  },
  data: () => ({
    project: [
      {
        name: 'Website Redesign',
        img: 'https://upload.wikimedia.org/wikipedia/commons/thumb/b/b2/Bootstrap_logo.svg/512px-Bootstrap_logo.svg.png',
        process: 'In progress',
        totalBudget: 7600,
        currency: 'USD',
      },
      {
        name: 'Website Redesign',
        img: 'https://upload.wikimedia.org/wikipedia/commons/thumb/b/b2/Bootstrap_logo.svg/512px-Bootstrap_logo.svg.png',
        process: 'In progress',
        totalBudget: 7600,
        currency: 'USD',
      },
      {
        name: 'Website Redesign',
        img: 'https://upload.wikimedia.org/wikipedia/commons/thumb/b/b2/Bootstrap_logo.svg/512px-Bootstrap_logo.svg.png',
        process: 'In progress',
        totalBudget: 7600,
        currency: 'USD',
      },
      {
        name: 'Website Redesign',
        img: 'https://upload.wikimedia.org/wikipedia/commons/thumb/b/b2/Bootstrap_logo.svg/512px-Bootstrap_logo.svg.png',
        process: 'In progress',
        totalBudget: 7600,
        currency: 'USD',
      },
      {
        name: 'Website Redesign',
        img: 'https://upload.wikimedia.org/wikipedia/commons/thumb/b/b2/Bootstrap_logo.svg/512px-Bootstrap_logo.svg.png',
        process: 'In progress',
        totalBudget: 7600,
        currency: 'USD',
      },
      {
        name: 'Website Redesign',
        img: 'https://upload.wikimedia.org/wikipedia/commons/thumb/b/b2/Bootstrap_logo.svg/512px-Bootstrap_logo.svg.png',
        process: 'In progress',
        totalBudget: 7600,
        currency: 'USD',
      },
    ]
  })
}
</script>


<style lang="scss">
$color-body: rgb(248, 243, 253);

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background-color: $color-body;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  // text-align: center;
  color: #2c3e50;
  margin-left: 280px;

  //yiğithan

  display: flex;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}


  /* width */
::-webkit-scrollbar {
  width: 10px;
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
