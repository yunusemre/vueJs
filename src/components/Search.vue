<template>
	<div class="search">
		<input placeholder="Hüüüloooooğğğğğğğğ" type="text" v-model="query" @keypress.enter="handleSearch"/>
		<button  @click="handleSearch">Search</button>
	</div>
</template>

<script>
	export default {
		data () {
			return {
				query: 'patron çıldırdı'
			}
		},
		methods: {
			handleSearch(){
				this.$emit('SearchRequested', this.query);
			}
		}
	}
</script>


<style>
	.search input {
		padding: 10px;
		border-radius: 4px;
		border: 1px solid #ddd;
		width: 300px;
	}

  .search input:focus, .search input:active {
    border: 1px solid #d9edf7;
	}

	.search button {
		padding: 8px;
    background: #fff;
    border: 0;
    border-radius: 4px;
    color: #666;
    font-size: 14px;
    border: 1px solid #ddd;
	}

</style>
