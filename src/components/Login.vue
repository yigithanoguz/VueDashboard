<template>
  <div class="login">
    <LoginTopBar />
    <!-- <ProjectsTabs /> -->

    <div class="form">
      <form @submit.prevent="onSubmit">
        <label>Email </label>
        <input type="text" v-model="login.email" />

        <label>Password </label>
        <input type="password" v-model="login.password" />

        <br />
        <button type="submit">Login</button>
      </form>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import LoginTopBar from "./LoginTopBar.vue";
// import ProjectsTabs from "./ProjectsTabs.vue";

export default {
  name: 'login',
  data() {
    return {
      login: {
        email: '',
        password: '',
      },
    };
  },
  methods: {
    onSubmit() {
      let email = this.login.email;
      let password = this.login.password;
      axios.get('https://6293500f089f87a57abdf537.mockapi.io/user')
      .then(response => {
        let data = response.data;
        for(let key in data) {
          if(data[key].email === email && data[key].password === password) {
            this.login = data[key];
            console.log(this.login);
            this.$emit('user', this.login);
            return console.log('Giriş başarılı...');
          }
        }
        console.log('Hatalı giriş...');
      })
    },
  },
  components: {
    LoginTopBar,
    // ProjectsTabs,
  },
};
</script>

<style lang="scss" scoped>

$color-input-bg: rgb(252, 245, 255);
$color-input-border: rgb(123, 92, 172);
$color-input-border-focus: rgb(92, 66, 134);
$color-button-bg: rgb(123, 92, 172);
$color-button-bg-hover: rgb(92, 66, 134);

.login {

  .form {
    padding: 20px;

    form {
      display: flex;
      flex-direction: column;
      padding: 0 5%;
      gap: 10px;

      input[type="text"],
      input[type="email"],
      input[type="password"] {
        height: 35px;
        padding: 10px;
        font-size: 1rem;
        outline: none;
        border-radius: 8px;
        background-color: $color-input-bg;
        border: solid 1px $color-input-border;

        &:focus {
          border: solid 2px $color-input-border-focus;
        }
      }

      button {
        border: none;
        color: rgb(246, 246, 246);
        font-weight: bold;
        font-size: 14px;
        background-color: $color-button-bg;
        cursor: pointer;
        height: 35px;
        border-radius: 14px;
        transition: 0.3s;

        &:hover {
          background-color: $color-button-bg-hover;
        }

      }

      select {
        height: 35px;
        border-radius: 8px;
        outline: none;
        border: solid 1px $color-input-border;
        background-color: $color-input-bg;

        &:focus {
          border: solid 2px $color-input-border-focus;
        }

      }

    }
  }
}

</style>
