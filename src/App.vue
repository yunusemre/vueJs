<template>
  <div id="app">
    <nav>
      Müminsiz Gif
    </nav>
    <search v-on:SearchRequested="handleSearch"></search>
    <p v-if="is_loading">Loading...</p>
    <p class="warning" v-if="no_content">Oooo my god. You falled in boiler :)</p>
    <preview :gifs="gifs"></preview>
  </div>
</template>

<script>

import Search from './components/Search.vue'
import Preview from './components/Preview.vue'

export default {
	name: 'app',
	components: { Search, Preview },
	data(){
		return {
			is_loading: true,
			no_content: false,
			gifs: []
		}
	},
	methods: {
		doSearch(url){
			fetch(url)
			.then((res)=> {return res.json()})
			.then((res)=> { this.gifs = res.data })
			.then((res) => {
				this.is_loading = false;
				if(this.gifs.length == 0){
					this.no_content = true;
				}
			});
		},
		handleSearch(query){
			this.gifs = [];
			this.is_loading = true;
			this.no_content = false;
			const url = 'http://api.giphy.com/v1/gifs/search?q='+ query +'&api_key=dc6zaTOxFJmzC'
			this.doSearch(url);
		}
	},
	created(){
		const url = 'http://api.giphy.com/v1/gifs/trending?api_key=dc6zaTOxFJmzC'
		this.doSearch(url);
	}
}
</script>

<style>
	#app {
		font-family: 'Avenir', Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		color: #2c3e50;
		text-align: center;
		padding: 0 10px 10px 10px;
	}

	nav {
		background: white;
		text-align: center;
		margin-bottom: 40px;
		border-bottom: 1px solid #ddd;
		padding-top : 10px;
		padding-bottom : 10px;
		font-size: 36px;
		border-radius: 4px;
	}

	.warning { color: red; font-weight: bold;}

</style>
