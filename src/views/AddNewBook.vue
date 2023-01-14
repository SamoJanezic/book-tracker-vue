<template>
  
	<h3>Here you can add a new book</h3>
  <form class="form-container">
		<label class="item">Title: </label>
		<input type="text" v-model="book.title" /> <br>

    <label class="item">Author: </label>
    <input type="text" v-model="book.author" /><br>

    <label class="item">Pages: </label>
    <input type="text" v-model="book.pages" /><br>

    <label class="item">Publisher: </label>
    <input type="text" v-model="book.publisher" /><br>

    <label class="item">Publication year: </label>
    <input type="text" v-model="book.publicationYear" /><br>

    <label class="item">Image url: </label>
    <input type="text" v-model="book.image" />
	</form>
  <button @click="showInput">Add Book</button>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import './AddNewBook.css';

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
      console.log(this.book)
    },

    // addBook() {

    // }
  }
});
</script>
