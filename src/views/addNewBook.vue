<template>
	<h3>Here you can add a new book</h3>
  <form>
		<label>Title: </label>
		<input type="text" v-model="book.title" /> <br>
    <label>Author: </label>
    <input type="text" v-model="book.author" /><br>
    <label>Pages: </label>
    <input type="text" v-model="book.pages" /><br>
    <label>Publisher: </label>
    <input type="text" v-model="book.publisher" /><br>
    <label>Publication year: </label>
    <input type="text" v-model="book.publicationYear" /><br>
    <label>Image url: </label>
    <input type="text" v-model="book.image" />
	</form>
  <div>{{ book.title }}</div>
  <button @click="showInput">Add Book</button>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
	name: 'addBook',
	data() {
		return {
      book: {
        title: '',
        author: '',
        pages: '',
        publisher: '',
        publicationYear: '',
        image: ''
      }
    };
	},
  methods: {
    showInput() {
      console.log(this.book);
    },
    // addBook() {

    // }
  }
});
</script>
