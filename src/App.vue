<template>
	<div>
		<img alt="Vue logo" src="./assets/logo.png" />

		<book-form @book-added="addBook"></book-form>

		<ul>
			<li v-for="book in books" :key="book.title">
				<book :title="book.title" :author="book.author" :genre="book.genre"></book>
			</li>
		</ul>
	</div>
</template>

<script>
import Book from "./components/Book.vue";
import BookForm from "./components/BookForm.vue";
import BookList from "./assets/stack.json";

export default {
	name: "App",
	components: {
		Book,
		BookForm,
	},
	data() {
		return {
			books: BookList,
		};
	},
	methods: {
		addBook(title, author, genre) {
			this.books.push({ title: title, author: author, genre: genre });
			//save to stacks.json
			var fs = require("fs");
			try {
				fs.write("stack.json", this.authorbooks);
				console.log("Saved to stack.json.");
			} catch (err) {
				console.error(err);
			}
		},
	},
};
</script>

<style>
/* End global styles */
#app {
	background: #fff;
	margin: 2rem 0 4rem 0;
	padding: 1rem;
	padding-top: 0;
	position: relative;
	box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.2), 0 2.5rem 5rem 0 rgba(0, 0, 0, 0.1);
}
@media screen and (min-width: 550px) {
	#app {
		padding: 4rem;
	}
}
#app > * {
	max-width: 50rem;
	margin-left: auto;
	margin-right: auto;
}
#app > form {
	max-width: 100%;
}
#app h1 {
	display: block;
	min-width: 100%;
	width: 100%;
	text-align: center;
	margin: 0;
	margin-bottom: 1rem;
}
</style>
