<template>
	<form id="bookForm" @submit.prevent="onSubmit">
		<div>
			<label>Enter Title</label>&nbsp;
			<input type="text" id="book-title" name="new-book-title" v-model.lazy.trim="title" ref="title" />
		</div>
		<div>
			<label>Enter Author</label>&nbsp;
			<input type="text" id="book-author" name="new-book-author" v-model.lazy.trim="author" ref="author" autocomplete="off" />
		</div>
		<div>
			<label>Enter Genre</label>&nbsp;
			<input type="text" id="book-genre" name="new-book-benre" v-model.lazy.trim="genre" ref="genre" />
		</div>
		<div>
			<button type="submit">Add Book</button>
		</div>
	</form>
</template>
<script>
export default {
	methods: {
		onSubmit() {
			if (this.author === "" || this.title === "" || this.genre === "") {
				return;
			} else {
				this.$emit("book-added", this.title, this.author, this.genre);
			}
			this.$refs["title"].value = "";
			this.$refs["author"].value = "";
			this.$refs["genre"].value = "";
		},
		data() {
			return {
				title: "",
				author: "",
				genre: "",
			};
		},
	},
};
</script>
