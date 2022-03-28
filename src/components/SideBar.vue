<template>
	<div>
		<div class="bar bg-danger">
			<h2 class="pt-3">Mapa de Joinville</h2>
			<h3 v-if="!districtInfo">Selecione um bairro</h3>
			<ul v-else class="list mt-4">
				<li class="districtTitle pb-2">{{ districtInfo.name }}</li>
				<li>População: {{ districtInfo.population }}</li>
				<li>Densidade: {{ districtInfo.density }} hab/km²</li>
				<li>Área: {{ districtInfo.area }} km²</li>
			</ul>
		</div>
	</div>
</template>
<script>
export default {
	name: 'SideBar',
	props: {
		districtInfo: {
			type: Object,
		},
	},
};
</script>
<style scoped>
.bar {
	width: 100%;
	height: 100vh;
	/* background-color: black; */
}
h2 {
	font-size: 2.5rem;
	font-weight: bold;
	color: white;
	text-align: center;
}
h3 {
	text-align: center;
	font-weight: bold;
}
.list {
	font-size: 1.5rem;
	list-style: none;
}
.districtTitle {
	font-weight: bold;
	font-size: 1.7rem;
}
</style>
