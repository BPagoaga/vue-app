<template>

<div class="form-group">		
	<brand-selector v-on:change.native="getModels($event.target.value)" name="brand-selector" message="Choisissez votre marque" :data="brands" ></brand-selector>
	<model-selector v-on:change.native="getMotorisations($event.target.value)" name="model-selector" message="Choisissez votre modèle" :data="models"></model-selector>
	<motor-selector name="motor-selector" message="Choisissez votre motorisation" :data="motorisations"></motor-selector>
</div>

</template>
<script>
	import BrandSelector from './BrandSelector.vue'
	import ModelSelector from './ModelSelector.vue'
	import MotorSelector from './MotorSelector.vue'

	export default {
		props: {
			brands: { type: Array }
		},
		data() {
			return {
				models: [],
				motorisations: [],
			}
		},
		components: {
			'brand-selector': BrandSelector,
			'model-selector': ModelSelector,
			'motor-selector': MotorSelector
		},
		methods: {
			getModels(brand_id){
				var self = this
				this.getSubData(brand_id, '/posts?userId=')
				.then(function(data){
					self.models = data
				})
			},
			getMotorisations(model_id){
				var self = this
				this.getSubData(model_id, '/comments?postId=')
				.then(function(data){
					self.motorisations = data
				})
			},
			getSubData(id, req){
				const params = { method: 'GET'}
		        const baseUrl = 'https://jsonplaceholder.typicode.com';
		        
		        return fetch(baseUrl + req + id)
		        .then(response => {
	                return response.json()
	            })
	            .catch(function(error) {
	                console.log('Il y a eu un problème avec l\'opération fetch: ' + error.message);
	            })
			}
		}
	}
</script>