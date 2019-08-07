<template>
  <div class="books-new">
    <h1>{{ message }}</h1>
    <form v-on:submit.prevent="createBook()">
      <p>Title: <input type="text" v-model="newBookTitle"></p>
      <p>Pages: <input type="text" v-model="newBookPages"></p>
      <input type="submit" value="Create Book">
    </form>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      message: "Create a New Book",
      newBookTitle: "",
      newBookPages: ""
    };
  },
  created: function() {},
  methods: {
    createBook: function() {
      var newBook = {
        title: this.newBookTitle,
        pages: this.newBookPages
      };
      axios.post('/api/books', newBook).then(response => {
        console.log("in the callback for create");
        console.log(response.data);
      });
    }
  }
};
</script>