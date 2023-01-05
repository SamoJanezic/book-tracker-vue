<template>
	<h3>Here you can add a new book</h3>
  <form class="grid-container">
		<label class="grid-item grid-item-1">Title: </label>
		<input type="text" v-model="book.title" /> <br>

    <label class="grid-item grid-item-1">Author: </label>
    <input type="text" v-model="book.author" /><br>

    <label class="grid-item grid-item-1">Pages: </label>
    <input type="text" v-model="book.pages" /><br>

    <label class="grid-item grid-item-1">Publisher: </label>
    <input type="text" v-model="book.publisher" /><br>

    <label class="grid-item grid-item-1">Publication year: </label>
    <input type="text" v-model="book.publicationYear" /><br>
    
    <label class="grid-item grid-item-1">Image url: </label>
    <input type="text" v-model="book.image" />
	</form>
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
