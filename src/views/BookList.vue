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
				<td><span>edit</span> | <span>delete</span></td>
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
		getItem(items: any) {
			axios
				.get('https://127.0.0.1:49178/json')
				.then(function (response: any) {
					// handle success
					const data = response.data;
					const recieved = Object.values(data).map((val) => {
						items.push(val);
					});
				})
				.catch(function (error: string) {
					// handle error
					console.log(error);
				})
				.then(() => {
					this.loading = false;
				});
		},
	},
	mounted() {
		this.getItem(this.books);
	},
});
</script>
