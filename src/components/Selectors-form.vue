<template>
<form action="">
	<div class="form-group">		
		<brand-selector v-on:select="test" name="brand-selector" message="Choisissez votre marque" :data="selectPosts"></brand-selector>
		<model-selector name="model-selector" message="Choisissez votre modèle" :data="selectPosts"></model-selector>
		<motor-selector name="motor-selector" message="Choisissez votre motorisation" :data="selectPosts"></motor-selector>
	</div>
</form>
</template>
<script>
	import BrandSelector from './BrandSelector.vue'
	import ModelSelector from './BrandSelector.vue'
	import MotorSelector from './BrandSelector.vue'

	export default {
		props: {
			selectPosts: { type: Array }
		},
		data() {
			return {}
		},
		components: {
			'brand-selector': BrandSelector,
			'model-selector': ModelSelector,
			'motor-selector': MotorSelector
		},
		methods: {
			test() {
				console.log('test')
			}
		}
	}
</script>