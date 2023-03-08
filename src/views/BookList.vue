<template>
	<span v-if="loading">...Loading</span>
	<div v-else>
		<table>
			<tr>
				<th></th>
				<th>ID</th>
				<th>Title</th>
				<th>Series</th>
				<th>Author</th>
				<th>Pages</th>
				<th>Publisher</th>
				<th>Publication year</th>
				<th>Image</th>
			</tr>
			<tr v-for="book in books" :key="book.id">
				<td><span class="listBtn" @click="showItem">edit</span> | <span class="listBtn" @click="deleteItem(book.id, this.books)">delete</span></td>
				<td>{{ book.id }}</td>
				<td>{{ book.title }}</td>
				<td>{{ book.series }}</td>
				<td>{{ book.author }}</td>
				<td>{{ book.pages }}</td>
				<td>{{ book.publisher }}</td>
				<td>{{ book.publicationYear }}</td>
				<td class="image-container">
					<img class="table-image" :src="book.image" alt="Book Image" />
				</td>
			</tr>
		</table>
	</div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import './BookList.css';
import axios from 'axios';

export default defineComponent({
	data() {
		return {
			loading: true,
			books: [],
		};
	},
	methods: {
		changeStatus() {
			this.loading = false;
		},
		showItem() {
			console.log(this.books);
		},
		addBook(title, author, description, pages, publisher, publicationYear, image, series) {
			axios.post(`https://booklist.ddev.site/book/add?title=${title}&author=${author}&description=${description}&pages=${pages}&publisher=${publisher}&publicationYear=${publicationYear}&image=${image}&series=${series}`)
			.catch((error: string) => {
				console.log(`There was an error POSTING the book: ${error}`)
			});
		},
		deleteItem(id: number, items: object) {
			this.books = [];
			axios
				.get(`https://booklist.ddev.site/book/delete?id=${id}`)
				.then((response) => {
					this.getBooks(this.books);
				})
				// .then(this.getBooks(this.books))
				.catch((error: string) => {
					console.log(`There was an error DELETING the book: ${error}`);
				});
		},
		getBooks(items: any) {
			axios
				.get('https://booklist.ddev.site/book/list')
				.then((response: any) => {
					const data = response.data;
					Object.values(data).forEach((val) => {
						items.push(val);
					});
				})
				.catch((error: string) => {
					console.log(`There was an error GETTING the list: ${error}`);
				})
				.then(() => {
					this.loading = false;
				});
		},
	},
	mounted() {
		this.getBooks(this.books);
	},
});
</script>
