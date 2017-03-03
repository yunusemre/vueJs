<template>
  	<div class="preview">
		<ul>
			<li v-for="gif in gifs">
				<img :src="gif.images.fixed_height.url" alt="gif.images.fixed_height.name">
			</li>
		</ul>
  	</div>
</template>

<script>
	export default {
		props: ['gifs']
	}
</script>

<style>
  	ul {
    	padding: 0;
  	}
  	li {
    	display: inline-block;
    	padding: 0 10px 10px 0;
  	}
</style>
