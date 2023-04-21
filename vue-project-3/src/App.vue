<script>
import axios from "axios"
export default {
  data() {
    return {
      count: null,
      info: {}
    }
  },
  created() {
    this.getToDos();
  },
  methods: {
    getToDos() {
      axios.get("https://jsonplaceholder.typicode.com/todos/")
          .then(response => {
            this.info = response.data;
          });
    },
    deleteToDos(id) {
      this.info.splice(id, 1);
    }
  }
}
</script>

<template>
  <td>
    <input type="number" v-on:input="count = $event.target.value">
    <button @click="deleteToDos(this.count)">Delete</button>
  </td>
  <h1>{{info}}</h1>
</template>

<style scoped>
h1 {
  color: black;
}
</style>
