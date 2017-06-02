<template>
<div id="app">
    <div class="container">
        <selectors-form :select-posts="posts"></selectors-form>
    </div>
</div>
</template>
<script>
import selectorsForm from './components/Selectors-form.vue';

export default {
    name: 'app',
    data () {
        return {
            posts: []
        }
    },
    mounted() {
        const params = { method: 'POST'}
        const baseUrl = 'https://jsonplaceholder.typicode.com';
        
        fetch(baseUrl + '/posts')
            .then(response => {
                return response.json()
            })
            .then(data => {
                this.posts = data
            })
            .catch(function(error) {
                console.log('Il y a eu un problème avec l\'opération fetch: ' + error.message);
            })
            
    },
    components: {
        'selectors-form' : selectorsForm
    }
}
</script>
<style>
#app {
font-family: 'Avenir', Helvetica, Arial, sans-serif;
-webkit-font-smoothing: antialiased;
-moz-osx-font-smoothing: grayscale;
text-align: center;
color: #2c3e50;
margin-top: 60px;
}
h1, h2 {
font-weight: normal;
}
ul {
list-style-type: none;
padding: 0;
}
li {
display: inline-block;
margin: 0 10px;
}
a {
color: #42b983;
}
</style>