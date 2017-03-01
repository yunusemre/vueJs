<template>
  <div class="Home">
    <nav>
		<ul>
			<li v-for="data in datas">
				<router-link :to="data.url">{{data.name}}</router-link>
			</li>
		</ul>
    </nav>
	<div class="container">
		{{msg}}
	</div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data () {
    return {
      msg: 'Home Page',
      datas: [
        {'name': 'Home', 'url': '/home'},
        {'name': 'About', 'url': '/about'}
      ]
    }
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

a[href] { color: darkred; text-decoration: none;}
nav {
	position: fixed;
	width: 100%;
	padding: 0 0 10px 0; 
	top: 0;
	left: 0;
	background: #eee;
	border-bottom: 1px solid #ddd;
}

nav ul { list-style: none; padding: 0;}
nav ul li {
	float: left;
	margin: 0 10px;
}
</style>