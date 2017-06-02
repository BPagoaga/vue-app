<template>
	<select :name="name" class="form-control">
		<option value="">{{ message }}</option>
		<option value="" v-for="post in data">{{ post.title }}</option>
	</select>
</template>

<script>
	export default {
		props: {
			name: { type: String },
			message: { type: String },
			data: { type: Array }
		}
	}
</script>