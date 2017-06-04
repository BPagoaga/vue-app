<template>
	<select :name="name" class="form-control" @change="bubbleToApp">
		<option value="">{{ message }}</option>
		<option :value="motor.id" v-for="motor in data">Commentaire : {{ motor.body }}</option>
	</select>
</template>

<script>
import bus from '../bus.js'
// the motor in data is a comment
	export default {
		props: {
			name: { type: String },
			message: { type: String },
			data: { type: Array }
		},
		methods: {
			bubbleToApp(){
				console.log('will emit')
				bus.$emit('changedDisable', this.name)
			}
		}
	}
</script>