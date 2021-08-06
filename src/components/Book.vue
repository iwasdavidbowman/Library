<template>
	<div>
		<div>
			<label>Title: {{ title }}</label>
		</div>
		<div>
			<label>Author: {{ author }}</label>
		</div>
		<div>
			<label>Genre: {{ genre }}</label>
		</div>
        <div>
        <button type="button">Edit</button>
        </div>
	</div>
</template>

<script>
export default {
	props: {
		title: { required: true, type: String },
		author: { required: true, type: String },
		genre: { required: true, type: String },
	},
};
</script>
