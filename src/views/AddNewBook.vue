<template>
  <h3>Here you can add a new book</h3>
  <div id="add-book">
    <div>
      <form class="form-container">
        <label class="item">Title: </label>
        <input type="text" v-model="book.title" /> <br>

        <label class="item">Series: </label>
        <input type="text" v-model="book.series" /><br>

        <label class="item">Author: </label>
        <input type="text" v-model="book.author" /><br>

        <label class="item">Description:  </label>
        <textarea type="text" v-model="book.description" /><br>

        <label class="item">Pages: </label>
        <input type="number" v-model="book.pages" /><br>

        <label class="item">Publisher: </label>
        <input type="text" v-model="book.publisher" /><br>

        <label class="item">Publication year: </label>
        <input type="number" v-model="book.publicationYear" /><br>

        <label class="item">Image url: </label>
        <input type="text" v-model="book.image" />
      </form>
      <button @click="showInput">Add Book</button>
    </div>
    <div class="image-container">
      <span>Book-link: </span>
      <img src="https://www.emka.si/wcsstore/MKCAS/img/product/leposlovje/fantazijska-literatura/365187/9780575081406_500.jpg" alt="book-image">
    </div>
  </div>
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
        description: '',
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
