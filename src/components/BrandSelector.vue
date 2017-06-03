<template>
	<select :name="name" class="form-control">
		<option value="">{{ message }}</option>
		<option value="" v-for="post in data" v-on:select="selectPost($event.target.value)">{{ post.title }}</option>
	</select>
</template>

<script>
	export default {
		props: {
			name: { type: String },
			message: { type: String },
			data: { type: Array }
		},
		methods: {
			selectPost(id) {
				console.log("select")
				this.$emit('select', id)
			}
		}
	}
</script>