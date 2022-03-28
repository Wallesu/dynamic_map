<template>
	<div id="app">
		<div class="row m-0">
			<div class="col-3 m-0 p-0">
				<SideBar :districtInfo="districtInfo"></SideBar>
			</div>
			<div class="col-9 m-0 p-0">
				<div class="row m-0">
					<Map @sendDistrictInfo="getDistrictInfo"></Map>
				</div>
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
	data() {
		return {
			districtInfo: '',
		};
	},
	methods: {
		getDistrictInfo(value) {
			this.districtInfo = value;
		},
	},
};
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	color: #2c3e50;
}
h1 {
}
body {
	background-color: #bde4e5;
}

@import '~bootstrap/dist/css/bootstrap.css';
</style>
