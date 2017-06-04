<template>
	<select :name="name" class="form-control">
		<option value="">{{ message }}</option>
		<option :value="brand.id" v-for="brand in data">{{ brand.name }}</option>
	</select>
</template>

<script>
// the brand in data is a user
	export default {
		props: {
			name: { type: String },
			message: { type: String },
			data: { type: Array }
		}
	}
</script>