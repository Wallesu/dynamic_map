<template>
	<g
		:id="id"
		:data-name="dataName"
		:population="population"
		:density="density"
		:area="area"
		@click="showInfo($event)"
		class="bairro"
	>
		<path class="bairro" :d="path" />
	</g>
</template>
<script>
export default {
	name: 'district',
	data() {
		return {};
	},
	props: {
		id: {
			default: null,
		},
		dataName: {
			default: null,
		},
		population: {
			default: null,
		},
		density: {
			default: null,
		},
		area: {
			default: null,
		},
		path: {
			default: null,
		},
	},
};
</script>
<style scoped>
.bairro:hover {
	fill: rgb(177, 31, 177);
}

.bairro {
	stroke-width: 1;
	stroke: white;
}

g {
	fill: #ee8fab;
}

.bairro:hover {
	fill: #ff004c;
	z-index: 100;
}
</style>
