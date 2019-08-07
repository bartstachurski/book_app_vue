<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div v-for="book in books">
      <p>Title: {{ book.title }}</p>
      <p>Pages: {{ book.pages }}</p>
    </div>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      message: "Books Index",
      books: {}
    };
  },
  created: function() {
    axios.get("/api/books").then(response => {
      console.log(response.data);
      this.books = response.data;
    });
  },
  methods: {}
};
</script>