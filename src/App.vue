<template>
	<div id="app">
		<div class="row m-0">
			<div class="col-4 m-0 p-0">
				<SideBar></SideBar>
			</div>
			<div class="col-4 m-0 p-0">
				<Map />
			</div>
		</div>
	</div>
</template>

<script>
import Map from './components/Map.vue';
import SideBar from './components/SideBar.vue';

export default {
	name: 'App',
	components: {
		Map,
		SideBar,
	},
};
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	color: #2c3e50;
}
body {
	background-color: #bde4e5;
}
@import '~bootstrap/dist/css/bootstrap.css';
</style>
