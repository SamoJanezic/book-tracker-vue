<template>
  <table>
    <tr>
      <th></th>
      <th>ID</th>
      <th>Title</th>
      <th>Author</th>
      <th>Pages</th>
      <th>Publisher</th>
      <th>Publication year</th>
      <th>Image</th>
    </tr>
    <tr v-for="book in books" :key="book.id">
      <td><span>edit</span> | <span>delete</span></td>
      <td>{{ book.id + 1 }}</td>
      <td>{{ book.title }}</td>
      <td>{{ book.author }}</td>
      <td>{{ book.pages }}</td>
      <td>{{ book.publisher }}</td>
      <td>{{ book.publicationYear }}</td>
      <td class="image-container">
        <img class="table-image" :src="book.image" alt="Book Image" />
      </td>
    </tr>
  </table>
</template>

<script lang="ts">
  import { defineComponent } from 'vue';
  import './BookList.css';

  export default defineComponent({
    data() {
      return {
        books: [
          {
            id: 0,
            title: 'The Blade Itself',
            author: 'Joe Abercrombie',
            pages: 672,
            publisher: 'Tor Books',
            publicationYear: 2006,
            image:
              'https://www.gollancz.co.uk/wp-content/uploads/2018/07/hbg-title-9780575089914-669.jpg?fit=442%2C675',
          },
          {
            id: 1,
            title: 'Mistborn: the Final Empire',
            author: 'Brandon Sanderson',
            pages: 560,
            publisher: 'Gollancz',
            publicationYear: 2006,
            image:
              'https://images-na.ssl-images-amazon.com/images/S/compressed.photo.goodreads.com/books/1284167912l/944073.jpg',
          },
          {
            id: 2,
            title: 'Gardens of the Moon',
            author: 'Steven Erikson',
            pages: 712,
            publisher: 'Bantam',
            publicationYear: 1999,
            image: 'https://mpd-biblio-covers.imgix.net/9780765348784.jpg?w=900',
          },
          {
            id: 3,
            title: '1984',
            author: 'George Orwell',
            pages: 328,
            publisher: 'Secker & Warburg',
            publicationYear: 1948,
            image:
              'https://images.booksense.com/images/935/262/9780452262935.jpg',
          },
        ],
      };
    },
    methods: {},
  });
</script>
