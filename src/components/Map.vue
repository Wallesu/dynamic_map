<template>
	<div class="container d-flex justify-content-center my-0">
		<svg
			id="svg"
			class="map_container"
			xmlns="http://www.w3.org/2000/svg"
			viewBox="10 70 955 1750.83333333"
			@mousemove="getPositions($event)"
		>
			<District
				v-for="(district, i) in districts"
				:key="i"
				:info="district"
				@click.native="getInfos($event), (districtClicked = i)"
				:class="{
					'district-active': districtClicked == i,
					invisible:
						districtClicked != null &&
						districtClicked != i &&
						isZoom,
					zoomed: districtClicked == i && isZoom,
				}"
			></District>
		</svg>
		<div class="cordinate">
			{{ cordinate.x != 'NaN' ? cordinate : '' }}
		</div>
	</div>
</template>

<script>
import District from './District.vue';
import districtsData from '../districts-data.json';
export default {
	name: 'Map',
	components: {
		District,
	},
	props: {
		isZoom: {
			default: false,
		},
	},
	data() {
		return {
			bairro_nome: null,
			pointerLocation: {
				x: 0,
				y: 0,
			},
			svgPosition: {
				x: 0,
				y: 0,
			},
			svgSize: {
				width: 0,
				height: 0,
			},
			districts: districtsData,
			districtClicked: null,
		};
	},
	computed: {
		cordinate() {
			let x1cm = this.svgSize.width / 90;
			let y1cm = this.svgSize.height / 165;

			let x_pointerInSvg = this.pointerLocation.x - this.svgPosition.x;
			let y_pointerInSvg = this.pointerLocation.y - this.svgPosition.y;

			let x_in_cm = (x_pointerInSvg * 20000) / x1cm;
			let y_in_cm = (y_pointerInSvg * 20000) / y1cm;

			let x_in_km = x_in_cm / 100000;
			let y_in_km = y_in_cm / 100000;

			return {
				x: Number(x_in_km.toFixed(2)),
				y: Number(y_in_km.toFixed(2)),
			};
		},
	},
	methods: {
		getPositions(event) {
			let svgPosition = document
				.getElementById('svg')
				.getBoundingClientRect();

			this.svgSize.width = svgPosition.width;
			this.svgSize.height = svgPosition.height;

			this.svgPosition.x = svgPosition.x;
			this.svgPosition.y = svgPosition.y;

			this.pointerLocation.x = event.x;
			this.pointerLocation.y = event.y;
		},
		getInfos(event) {
			let g = event.path[1];
			let name = g.getAttribute('data-name');
			let population = g.getAttribute('population');
			let density = g.getAttribute('density');
			let area = g.getAttribute('area');
			this.$emit('sendDistrictInfo', {
				name: name,
				population: population,
				density: density,
				area: area,
			});
		},
	},
};
</script>

<style scoped>
/* .zoomed {
	animation: teste 2.5s ease-in-out;
} */
/* @keyframes teste {
	to {
		z-index: 10;
		transform: scale(2);
		transform-origin: 0 700px;
	} */
/* } */
.map_container {
	/* width: 100%; */
	height: 100vh;
	/* border: 1px solid red; */
}
.cordinate {
	width: 15rem;
}

/* .bairro-active {
	fill: #ff004c !important;
} */
</style>
