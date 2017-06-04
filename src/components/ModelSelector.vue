<template>
	<select :name="name" class="form-control">
		<option value="">{{ message }}</option>
		<option :value="model.id" v-for="model in data">Titre du post : {{ model.title }}</option>
	</select>
</template>

<script>
// the model in data is a post
	export default {
		props: {
			name: { type: String },
			message: { type: String },
			data: { type: Array }
		}
	}
</script>