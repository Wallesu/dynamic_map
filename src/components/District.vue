<template>
	<g
		:id="info.id"
		:data-name="info['data-name']"
		:population="info.population"
		:density="info.density"
		:area="info.area"
		class="district"
	>
		<path :d="info.path" />
	</g>
</template>
<script>
export default {
	name: 'district',
	data() {
		return {};
	},
	props: {
		info: {
			default: {},
		},
	},
};
</script>
<style scoped>
.district {
	stroke-width: 1;
	stroke: white;
	fill: #ee8fab;
	transition: 0.3s;
	transform-origin: 50% 50%;
	transform-box: fill-box;
}
.district:hover {
	fill: #ee7a9d;
}
.district-active {
	fill: #ff004c !important;
}
.invisible {
	display: none;
}
.zoomed {
	transform-origin: 0 0px;
	transform: scale(2);
	transform-origin: 50% 50%;
	transition: 0.3s;
	transform-box: fill-box;
}
</style>
