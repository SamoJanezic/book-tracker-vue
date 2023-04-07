<template>
	<span v-if="loading">...Loading</span>
	<div v-else>
		<table class="mainTable">
			<thead>
				<tr>
					<th></th>
					<th>ID</th>
					<th>Title</th>
					<th>Description</th>
					<th>Series</th>
					<th>Author</th>
					<th>Pages</th>
					<th>Publisher</th>
					<th>Publication year</th>
					<th>Image</th>
				</tr>
			</thead>
			<tbody v-for="book, idx in books" :key="idx" class="contentBox">
				<tr class="contentRow">
					<td><span class="listBtn" @click="showItem">edit</span> | <span class="listBtn" @click="deleteItem(book.id)">delete</span></td>
					<td>{{ book.id }}</td>
					<td>{{ book.title }}</td>
					<td>
						{{ book.description.substr(0, 45) }}...
						[<span
						class="listBtn"
						@click="showDescription(idx)">show more</span>]
					</td>
					<td>{{ book.series }}</td>
					<td>{{ book.author }}</td>
					<td>{{ book.pages }}</td>
					<td>{{ book.publisher }}</td>
					<td>{{ book.publicationYear }}</td>
					<!-- :class="{descBox: 'book.show'}" -->
					<td class="image-container">
						<img class="table-image" :src="book.image" alt="Book Image" />
					</td>
				</tr>
				<!-- <tr class="descBox" :class="{'descBoxSee': book.show}"> -->
				<tr v-if="book.show" class="descBox">

					<td colspan="2"><b>description:</b></td>
					<td colspan="8" class="desc">{{ book.description }}</td>
				</tr>
			</tbody>
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
		showDescription(idx: number) {
			//! Needs tidying
			this.books[idx].show == false ? this.books[idx].show = true : this.books[idx].show = false;
		},
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
		deleteItem(id: number) {
			this.books = [];
			axios
				.get(`https://booklist.ddev.site/book/delete?id=${id}`)
				.then(this.getBooks(() => this.books))
				.catch((error: string) => {
					console.log(`DELETE err: ${error}`);
				});
		},
		getBooks(items) {
			axios
				.get('https://booklist.ddev.site/book/list')
				.then((response) => {
					const data = response.data;
					Object.values(data).forEach((val, idx) => {
						items.push(val);
						this.books[idx].show = false;
					});
				})
				.catch((error: string) => {
					console.log(`GET err =  ${error}`);
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
