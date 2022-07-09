<template>
  <div>
    <form @submit.prevent="onSubmit">
      <label>Name: </label>
      <input type="text" v-model="post.name">
      <br />
      <label>Image Link: </label>
      <input type="text" v-model="post.img">
      <br />
      <label>Process: </label>
      <input type="text" v-model="post.process">
      <br />
      <label>Total Budget: </label>
      <input type="text" v-model="post.totalBudget">
      <br />
      <label>currency: </label>
      <input type="text" v-model="post.currency">
      <br />
      <button type="submit">Onayla</button>
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      post: {
        name: '',
        img: '',
        process: '',
        totalBudget: '',
        currency: '',
      }
    }
  },
  methods: {
    onSubmit() {
      axios.post('https://6293500f089f87a57abdf537.mockapi.io/project', { ...this.post })
        .then(response => {
          console.log(response)
        })
        .catch(e => console.log(e));
    }
  }
}
</script>
