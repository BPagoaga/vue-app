<template>
<div id="app">
    <div class="container">
        <form action="">
            <selectors-form :brands="users" @changedDisable="test(name)"></selectors-form>
            <input type="submit" name="" value="OK" @click.prevent="showResult" :disabled="disabled">
        </form>
    </div>
</div>
</template>
<script>
import selectorsForm from './components/Selectors-form.vue';
import bus from './bus.js'

export default {
    name: 'app',
    data () {
        return {
            users: [],
            disabled: true,
        }
    },
    created(){
        bus.$on('changedDisable', this.toggleDisabled)
    },
    mounted() {
        const params = { method: 'POST'}
        const baseUrl = 'https://jsonplaceholder.typicode.com';
        
        fetch(baseUrl + '/users')
            .then(response => {
                return response.json()
            })
            .then(data => {
                this.users = data
            })
            .catch(function(error) {
                console.log('Il y a eu un problème avec l\'opération fetch: ' + error.message);
            })
            
    },
    components: {
        'selectors-form' : selectorsForm
    },
    methods: {
        showResult() {
            console.log('results')
        },
        toggleDisabled(){
            return this.disabled = !this.disabled
        }
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
[type="submit"]{
    background-color: green;
}
[type="submit"]:disabled {
    background-color: red;
}

</style>