<template>
  <div class="login">
    <Login @user="user = $event" />
  </div>
</template>

<script>
// @ is an alias to /src
import Login from '../components/Login.vue';

export default {
  name: 'Home',
  components: {
    Login,
  },
  data() {
    return {
      user: {

      },
    }
  },
  methods: {
    sendUser() {
      this.$emit('user', this.user);
      this.sendUser();
    }
  },
  created() {
    this.sendUser();
  }
}
</script>
