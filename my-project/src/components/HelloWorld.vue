<template>
  <div>
    <form @submit.prevent="sendMessage">
      <input type="text" v-model="message">
      <button type="submit">Send</button>
    </form>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      message: ''
    };
  },
  methods: {
    sendMessage() {
      axios.post('http://127.0.0.1:5000/message', { message: this.message })
        .then(response => {
          console.log(response.data);
        })
        .catch(error => {
          console.error(error);
        });
    }
  }
};
</script>
