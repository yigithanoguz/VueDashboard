<template>
  <div class="create-project">
    <ProjectsTopBar />
    <ProjectsTabs />

    <div class="form">
      <form @submit.prevent="onSubmit">
        <label>Name </label>
        <input type="text" v-model="post.name" />
        <br />
        <label>Image Link </label>
        <input type="text" v-model="post.img" />
        <br />
        <label>Process </label>
        <input type="text" v-model="post.process" />
        <br />
        <label>Total Budget </label>
        <input type="text" v-model="post.totalBudget" />
        <br />
        <label>Choose a currency</label>
        <select v-model="post.currency">
          <option value="usd">$ - USD</option>
          <option value="euro">€ - Euro</option>
          <option value="sterlin">£ - Sterlin</option>
          <option value="tl">₺ - TL</option>
        </select>
        <br />
        <button type="submit">Onayla</button>
      </form>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import ProjectsTopBar from "./ProjectsTopBar.vue";
import ProjectsTabs from "./ProjectsTabs.vue";

export default {
  data() {
    return {
      post: {
        name: "",
        img: "",
        process: "",
        totalBudget: "",
        currency: "",
      },
    };
  },
  methods: {
    onSubmit() {
      axios
        .post("https://6293500f089f87a57abdf537.mockapi.io/project", {
          ...this.post,
        })
        .then((response) => {
          console.log(response);
        })
        .catch((e) => console.log(e));
    },
  },
  components: {
    ProjectsTopBar,
    ProjectsTabs,
  },
};
</script>

<style lang="scss" scoped>

$color-input-bg: rgb(252, 245, 255);
$color-input-border: rgb(123, 92, 172);
$color-input-border-focus: rgb(92, 66, 134);
$color-button-bg: rgb(123, 92, 172);
$color-button-bg-hover: rgb(92, 66, 134);

.create-project {
  .form {
    padding: 20px;

    form {
      display: flex;
      flex-direction: column;
      padding: 0 5%;

      input[type="text"] {
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
